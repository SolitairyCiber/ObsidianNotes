### Finding Targets	
-iL list.txt	using a text file to list servers
-sL targets	listing targets 
-n	no DNS lookup
	
### Host Discovery using ARP	
-sn targets	will not ping
-PR targets	no port scan
	Can use both of these together 
	
### TCP and UDP port discovery	
-PS<portnumber or numbers>	TCP SYN scan normally used with -sn
-PA<portnumber or numbers>	TCP ACK scan nurmally used with -sn
-PU<portumber or numbers>	UDP scan 

### Basic Scans	
-sT 	Full Open Connection sends rst-ack
-sS	Sends reset after syn-ack
	
### Fine Tuning	
-T0 through 5	0 is slow 5 is fastest
-p <port number or numbers>	
-p- 	all ports
	no ports do the top 1000
	
### Advanced	
-sN	Null bypass firewall
-sF	FIN also bypass firewall
-sX	xmas scan also bypass firewall
-f or -ff	fragments packets to fool IDS
-S <spoofed IP>	
-D <comma seperated list>	decoy include your IP in list
	
-sV	determine service/version info on open ports
-sV --version-light	try the most likely probes (2)
-sV --version-all	try all available probes (9)
-O	detect OS
--traceroute	run traceroute to target
--script=SCRIPTS	Nmap scripts to run
-sC or --script=default	run default scripts
-A	equivalent to -sV -O -sC --traceroute
-oN	save output in normal format
-oG	save output in grepable format
-oX	save output in XML format
-oA	save output in normal, XML and Grepable formats