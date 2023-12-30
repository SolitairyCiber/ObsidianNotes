Chopping Down the Proxy Log  

Log McBlue tells us that he has configured the Squid proxy server to use the following log format:

```session-shell
timestamp - source_ip - domain:port - http_method - http_uri - status_code - response_size - user_agent
```

Let's use one of the log entries as an example and compare it to the format above.

```session-shell
[2023/10/25:16:17:14] 10.10.140.96 storage.live.com:443 GET / 400 630 "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36"
```

|   |   |   |
|---|---|---|
|**Position**|**Field**|**Value**|
|1|Timestamp|[2023/10/25:16:17:14]|
|2|Source IP|10.10.140.96|
|3|Domain and Port|storage.live.com:443|
|4|HTTP Method|GET|
|5|HTTP URI|/|
|6|Status Code|400|
|7|Response Size|630|
|8|User Agent|"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36  <br>(KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36"|

As you can see in the table above, we can break the log entry down and assign a position to each value so that it can be easily interpreted. Now, let's continue by using another Linux command-line tool to split the log entries per column. This is the `cut` command.

The **cut** command allows you to extract specific sections (columns) of lines from a file or input stream by "cutting" the line into columns based on a delimiter and selecting which columns to display. This can be done using the `-d` option (for delimiter) and the `-f` for position. The example below uses space (' ') as its delimiter and only displays the timestamp (column #1 after cutting the log with space).

ubuntu@tryhackme: ~/Desktop/artefacts

```shell-session
ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f1 access.log
[2023/10/25:15:42:02]
[2023/10/25:15:42:02]
--- REDACTED FOR BREVITY ---
```

It's also possible to select multiple columns, just like in the example below, which chooses the timestamp (column #1), domain, port (column #3), and status code (column #6).

ubuntu@tryhackme: ~/Desktop/artefacts

```shell-session
ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f1,3,6 access.log
[2023/10/25:15:42:02] sway.com:443 200
[2023/10/25:15:42:02] sway.com:443 301
[2023/10/25:15:42:02] sway.office.com:443 200
--- REDACTED FOR BREVITY ---
```

Lastly, the space delimiter won't work if you plan to get the User-Agent column since its value may contain a space, just like in the example log:

`"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36"`

Given this, you must change the delimiter and select column #2 because the User-Agent is enclosed with double quotes.

ubuntu@tryhackme: ~/Desktop/artefacts

```shell-session
ubuntu@tryhackme:~/Desktop/artefacts$ cut -d '"' -f2 access.log
-
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36
-
--- REDACTED FOR BREVITY ---
```

In the example above, we used column #2 since column #1 will provide the contents before the first use of double quotes ("). Try executing `cut -d '"' -f1 access.log` and see how the output differs from the space delimiter.

Linux Pipes  

In the previous section, we introduced some Linux commands that will be useful for investigation. To utilise all these commands and produce an output that can provide meaningful information, we can use Linux Pipes.

In Linux or Unix-like operating systems, a **pipe** (or the "|" character) is a way to connect two or more commands to make them work together seamlessly. It allows you to take the **output** of one command and use it as the input for another command. We'll introduce more commands by going through some use cases.

1. **Get the first five connections made by 10.10.140.96.**
    
    To do this, we'll combine the **grep** command with the **head** command.
    
    **Grep** is a command in Linux that is used for searching text within files or input streams. It typically follows the syntax: `grep OPTIONS STRING_TO_SEARCH FILE_NAME`.
    
    Let's use the command to focus on the connections made by the specific IP by executing `grep 10.10.140.96 access.log`. To limit the display to the first five entries, we can append `| head -n 5` to that command to achieve our goal.
    
    ubuntu@tryhackme: ~/Desktop/artefacts
    
    ```shell-session
    ubuntu@tryhackme:~/Desktop/artefacts$ grep 10.10.140.96 access.log
    [2023/10/25:15:46:20] 10.10.140.96 flow.microsoft.com:443 CONNECT - 200 0 "-"
    --- REDACTED FOR BREVITY ---
    
    ubuntu@tryhackme:~/Desktop/artefacts$ grep 10.10.140.96 access.log | head -n 5
    [2023/10/25:15:46:20] 10.10.140.96 flow.microsoft.com:443 CONNECT - 200 0 "-"
    [2023/10/25:15:46:20] 10.10.140.96 flow.microsoft.com:443 GET / 307 488 "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36"
    [2023/10/25:15:46:20] 10.10.140.96 make.powerautomate.com:443 CONNECT - 200 0 "-"
    [2023/10/25:15:46:20] 10.10.140.96 make.powerautomate.com:443 GET / 200 3870 "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36"
    [2023/10/25:15:46:21] 10.10.140.96 o15.officeredir.microsoft.com:443 CONNECT - 200 0 "-"
    ```
    
    The first command's output may have been a little too overwhelming since it provides every connection made by the specific IP. Meanwhile, appending a pipe with a head command limited the results to five.
    
2. **Get the list of unique domains accessed by all workstations.**
    
    To do this, we'll combine the **sort** and **uniq** commands with the **cut** command.
    
    **Sort** is a Linux command used to sort the lines of text files or input streams in ascending or descending order, while the **uniq** command allows you to filter out and display unique lines from a sorted file or input stream. 
    
    **Note: The uniq command requires a sorted list to be effective because it only compares the adjacent lines.**
    
    To achieve our goal, we will start by getting the domain column and removing the port. When we have the list of domains, we'll sort it and get the unique list using the **sort** and **uniq** commands.
    
    ubuntu@tryhackme: ~/Desktop/artefacts
    
    ```shell-session
    # The first use of the cut command retrieves the column of the domain:port, and the second one removes the port by splitting it with a colon.
    
    ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f3 access.log | cut -d ':' -f1
    sway.com
    sway.com
    sway.office.com
    --- REDACTED FOR BREVITY ---
    
    # After retrieving the domains, the sort command arranges the list in alphabetical order
    
    ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f3 access.log | cut -d ':' -f1 | sort
    account.activedirectory.windowsazure.com
    account.activedirectory.windowsazure.com
    account.activedirectory.windowsazure.com
    --- REDACTED FOR BREVITY ---
    
    # Lastly, the uniq command removes all the duplicates
    
    ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f3 access.log | cut -d ':' -f1 | sort | uniq
    account.activedirectory.windowsazure.com
    activity.windows.com
    admin.microsoft.com
    --- REDACTED FOR BREVITY ---
    ```
    
    You can try to execute the commands one at a time to see their results before adding a piped command.
    
3. **Display the connection count made on each domain.**
    
    We already have the list of unique domains based on our previous use case. Now, we only need to add some parameters to our commands to get the count of each domain accessed. This can be done by adding the `-c` option to the **uniq** command.
    
    ubuntu@tryhackme: ~/Desktop/artefacts
    
    ```shell-session
    ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f3 access.log | cut -d ':' -f1 | sort | uniq -c
        423 account.activedirectory.windowsazure.com
        184 activity.windows.com
        680 admin.microsoft.com
        272 admin.onedrive.com
        304 adminwebservice.microsoftonline.com
    ```
    
    Moreover, the result can be sorted again based on the count of each domain by using the `-n` option of the **sort** command.
    
    ubuntu@tryhackme: ~/Desktop/artefacts
    
    ```shell-session
    ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f3 access.log | cut -d ':' -f1 | sort | uniq -c | sort -n
         78 partnerservices.getmicrosoftkey.com
        113 **REDACTED**
        118 ocsp.digicert.com
        123 officeclient.microsoft.com
    --- REDACTED FOR BREVITY ---
    ```
    
    Based on the result, you can see that the count of connections made for each domain is sorted in ascending order. If you want to make the output appear in descending order,  use the `-r` option. Note that it can also be combined with the `-n` option (`-nr` if written together).
    
    ubuntu@tryhackme: ~/Desktop/artefacts
    
    ```shell-session
    ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f3 access.log | cut -d ':' -f1 | sort | uniq -c | sort -nr
       4992 www.office.com
       4695 login.microsoftonline.com
       1860 www.globalsign.com
       1581 **REDACTED**
       1554 learn.microsoft.com
    --- REDACTED FOR BREVITY ---
    ```
    

You can play with all the above commands to test your capabilities in combining Linux commands using pipes.  

Hunting Down the Malicious Traffic

Now that we have developed the skills needed to assist Forensic McBlue, let's get down to business!

To start hunting for suspicious traffic, let's try to list the top domains accessed by the users and see if the users accessed any unusual domains. You can do this by reusing the previous command to retrieve the connection count for each domain and `| tail -n 10` to get the last 10 items.

ubuntu@tryhackme: ~/Desktop/artefacts

```shell-session
ubuntu@tryhackme:~/Desktop/artefacts$ cut -d ' ' -f3 access.log | cut -d ':' -f1 | sort | uniq -c | sort -n | tail -n 10
    606 docs.microsoft.com
    622 smtp.office365.com
    680 admin.microsoft.com
    850 c.bing.com
    878 outlook.office365.com
   1554 learn.microsoft.com
   1581 **REDACTED***
   1860 www.globalsign.com
   4695 login.microsoftonline.com
   4992 www.office.com
```

**Note: We used the command** `tail -n 10` **since the list is sorted in ascending order, and because of this, the domains with a high connection count are positioned at the end of the list.**

Check the list of domains and you'll see that Microsoft owns most of them. Out of the 10 domains we can see, one seems unusual. Let's use that domain with the grep and head commands to retrieve the first 10 connections made to it.  

ubuntu@tryhackme: ~/Desktop/artefacts

```shell-session
ubuntu@tryhackme:~/Desktop/artefacts$ grep **SUSPICIOUS DOMAIN** access.log | head -n 5 [2023/10/25:15:56:29] REDACTED_IP REDACTED_DOMAIN:80 GET /storage.php?goodies=aWQscmVjaXBpZW50LGdp 200 362 "Go-http-client/1.1"
[2023/10/25:15:56:29] REDACTED_IP REDACTED_DOMAIN:80 GET /storage.php?goodies=ZnQKZGRiZTlmMDI1OGE4 200 362 "Go-http-client/1.1"
[2023/10/25:15:56:29] REDACTED_IP REDACTED_DOMAIN:80 GET /storage.php?goodies=MDRjOGExNWNmNTI0ZTMy 200 362 "Go-http-client/1.1"
[2023/10/25:15:56:30] REDACTED_IP REDACTED_DOMAIN:80 GET /storage.php?goodies=ZTE3ODUsTm9haCxQbGF5 200 362 "Go-http-client/1.1"
[2023/10/25:15:56:30] REDACTED_IP REDACTED_DOMAIN:80 GET /storage.php?goodies=IENhc2ggUmVnaXN0ZXIK 200 362 "Go-http-client/1.1"
```

Upon checking the list of requests made to the **REDACTED** domain, we see something unusual with the string passed to the `goodies` parameter. Let's try to retrieve the data by cutting the request URI with equals (=) as its delimiter.

ubuntu@tryhackme: ~/Desktop/artefacts

```shell-session
ubuntu@tryhackme:~/Desktop/artefacts$ grep **SUSPICIOUS DOMAIN** access.log | cut -d ' ' -f5 | cut -d '=' -f2
aWQscmVjaXBpZW50LGdp
ZnQKZGRiZTlmMDI1OGE4
MDRjOGExNWNmNTI0ZTMy
ZTE3ODUsTm9haCxQbGF5
--- REDACTED FOR BREVITY ---
```

Based on the format, the data sent seems to be encoded with **Base64**. Using this theory, we can try to decode the strings by piping the output to a **base64** command.

ubuntu@tryhackme: ~/Desktop/artefacts

```shell-session
ubuntu@tryhackme:~/Desktop/artefacts$ grep **SUSPICIOUS DOMAIN** access.log | cut -d ' ' -f5 | cut -d '=' -f2 | base64 -d
id,recipient,gift
ddbe9f0258a804c8a15cf524e32e1785,Noah,Play Cash Register
cb597d69d83f24c75b2a2d7298705ed7,William,Toy Pirate Hat
4824fb68fe63146aabc3587f8e12fb90,Charlotte,Play-Doh Bakery Set
f619a90e1fdedc23e515c7d6804a0811,Benjamin,Soccer Ball
ce6b67dee0f69a384076e74b922cd46b,Isabella,DIY Jewelry Kit
939481085d8ac019f79d5bd7307ab008,Lucas,Building Construction Blocks
f706a56dd55c1f2d1d24fbebf3990905,Amelia,Play-Doh Kitchen
2e43ccd9aa080cbc807f30938e244091,Ava,Toy Pirate Map
--- REDACTED FOR BREVITY --- 
```

Did you notice that the decoded data seems to be sensitive data for AntarctiCrafts? This might be a case of data exfiltration!