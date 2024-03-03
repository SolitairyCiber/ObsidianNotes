> nmap -sV -Pn target.thm

### Check all ports.

> nmap -sV -Pn target.thm -p-

### Stealth scan. O flag is to identify OS.  

> **nmap -sS -O IPaddress

### Scripts.
 > **nmap --script**

 > nmap -sV --script=vulscan/vulscan.nse www.example.com

> nmap --script nmap-vulners/ -sV 11.22.33.44

> nmap -Pn --script vuln 192.168.1.105

