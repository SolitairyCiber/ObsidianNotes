## Identify the hash type
>python3 /usr/share/hash-identifier/hash-id.py

Or website https://www.tunnelsup.com/hash-analyzer/

## Identify the type number for hashcat
>hashcat -h | grep type from above

Or go to website https://hashcat.net/wiki/doku.php?id=example_hashes


## Crack a hash in a file
> hashcat -m IDnumber filenamewithhash /usr/share/wordlists/rockyou.txt

Save to file.
> hashcat -m IDnumber filenamewithhash /usr/share/wordlists/rockyou.txt | tee filename

Get a hash for wifi.

>sudo systemctl stop NetworkManager.service

> sudo systemctl stop wpa_supplicant.service

>sudo hcxdumptool -i wlan0 -o dumpfile.pcapng --active_beacon --enable_status=15

>sudo systemctl start wpa_supplicant.service

>sudo systemctl start NetworkManager.service

>hcxpcapngtool -o hash.hc22000 -E essidlist dumpfile.pcapng hashcat -m 22000 hash.hc22000 wordlist.txt

Windows:

>hashcat.exe -m 22000 hash.hc22000 -a 3 ?d?d?d?d?d?d?d?d hashcat.exe -m 22000 hash.hc22000 -a 3 --increment --increment-min 8 --increment-max 18 ?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d?d

