1.Backup kali's sources.list 
mv /etc/apt/sources.list /etc/apt/sources.list.bak 

2.Remove updates 
find /var/lib/apt/lists -type f -exec rm {} \; 

3.Change sources.list content 
sudo nano /etc/apt/sources.list 
Paste content given below 
deb [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbVFYUk4wMmhvaGhiOU9fSnZqRDVpX2RsN0NzUXxBQ3Jtc0tsVGMtSzAwWUt6VTFhZGdnaUxvdUE5MHpaSkx2WXhVdmFVbjVndURDU3MtNk1TVWVPMENuX3JicVVLWDZyX1gzWG1RUkJDNUlYLWhrVFhobUh1WTA5aEFZNi01SmZTUHlJY05ibHZHWTJpd2pBeXZwRQ&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqblM0aDkzbHFGc0ROZzdwRERVbVQtR2E5X3UyQXxBQ3Jtc0trMlFLZHIxc3owQjdlODFwWnplalFscTBkdTVGNnBpT29JQ200Rm81aE9tMDJZYjAwdnFOa2xnRlJMaE15eHRwQy1IRF9UUFJ6c2NoTktTWW55NUx6V3dUN1ZLSUJIbDBFTjQtRk9WTjk5ajZGYmNkYw&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa0IxQ3A3ZGtlY1cxSVpPYXJxODBudk5RWG1xUXxBQ3Jtc0ttTzdZS20xRzI4TzdRcGdKazFVb1R4QnF6cFJna2Z5cngyb2VRQzdJTjdoRlJSaXdFS2V2QnZTY291MXNQcUQ4SDZPM3lObGs1Q2o2YlBjSjJIWFpfeVZvdlNEWmVIblB6TlVpT1hIT2JTWGl4dEpXYw&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal-updates main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbVNlUUNOd3VZSHpnbFZLTmk4QmRVTU9kZ05JZ3xBQ3Jtc0tuTVhQUnNqR1FoQVR1bnhiVFBORjZycFhrLUhSRmNWWnk1T0ZlZC1jdG1tTzFvRmhOYWExLUdvd0ZXeXM2QkNMM3h4cTVZLV9wVnFtMDh6Qk1lQUhYWEx1MTI0ei0yMl8wVGVSSVFseFdpX3NTMkZGYw&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal-updates main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbUdJTmt6MkJOLWIyOWpwV1BxUHdhdnYycHdhUXxBQ3Jtc0ttcnlOd2FQWE1Xa21kMDFyaVBMZGxJVHNHZmFaTmMteUZOTUJPTEt4OWZzLTVGNWZqY3Mza3pQS09HRmZGSzFJWWhfVzVSVk9fa21ydzJza0Z2ZHdVNUV5RENTZkJjdFVoUWpGSXNOOVRnWTMxaHprdw&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal-security main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXNuZkE3d0w5STBSR3ZLS2U2c0ZDYWZEYzBnQXxBQ3Jtc0ttS2hWZmV6TXIyNkkxanhfWklJR2R5UlNMc19wMFloZlpIVkxnSk9wV0xsOF9jVklNcGU4V2FHY3Rrdmg5VzlhVkJ0UFJwalNkbU53aG03Y3hlMXRTM1R0TE1UZHg4SXV3TVdnWk9ocWJSb1gzU1d2OA&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal-security main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbUlPbVhrV01UR2UyZ1g5b1IyRVBZLWFERXlRQXxBQ3Jtc0tudW81S3FxS1FwZXhiUTAxbE1YVV9RckxPYThPUm45MWpXRzlRcmlyNUEyVzZ5aUhqMjUtLXBfUzZGQU5oaHNyYldUV2lVNDE1dmxaN19BZno0VUpWcnB0d1VJVG5LSC15QmVObWNkQVktTUVqa1NFTQ&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal-backports main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbXl0bnBHWW1MbmtyV2puMDVZYUJmazF6dzR3QXxBQ3Jtc0ttcndURndHTnVuMXJna05iYllCY1V6blNuMmRlTVhmZThQREZUandxVEE1R05rNnlQRjlJYXhtRUIwTVVHMWRYTEZQc3c4MWlFWnZEMzdLMDcyVWNEVXhjSURoLXl5b2NuRjR5bFZ6b1BDZUxMLUNkRQ&q=http%3A%2F%2Farchive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal-backports main restricted universe multiverse 
deb [http://archive.canonical.com/ubuntu](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbEtFVEFJMHJKaGRLUUlYU0Q2VFhXc3NhZEFld3xBQ3Jtc0ttRzdseWlVeXhWSDR4SVVHTVhNVERTQUVhNTVBcmx3ZURINEFnNmxaekJNZ3NzbHppeHVTeWVVdjI5R3d3Q3hlaWJPWUxFVC1zeDJzaGlSNEFRWnZsTmpHUUw2MVlWWGhpYzI2M2daSXhOaVlPSUxVSQ&q=http%3A%2F%2Farchive.canonical.com%2Fubuntu&v=7fSbzYsWD8Y) 
focal partner 
deb-src [http://archive.canonical.com/ubuntu](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbmtzblVVUG1tbUFQNm1vcU9PZWRHQVBTOTV4QXxBQ3Jtc0tua09wX1hpUHVJUWRHVXE4WTg2bHlOYkwzV3U1RHZuQzB2Ry15a0J0ZjRBVkQ4SlhaWE1uV2JNTUtvcl84U1pnM3RFVzkwZlFWZFVVZFVidE52TUVEdExETzRYOVpiREgtVnliSHdOLTdvZDBteDFxaw&q=http%3A%2F%2Farchive.canonical.com%2Fubuntu&v=7fSbzYsWD8Y) 
focal partner If you are using kali as a virtual machine then paste this instead As core Ubuntu repositories do not have the ARM repositories in them 
deb [arch=arm64] [http://ports.ubuntu.com/ubuntu-ports](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbTgyLWtOMkFaTHQzSDhjcGdjNVg5empoMUk2d3xBQ3Jtc0trbFB4THNuRTJ5MzJpaWRuZzBoelBOTFJzRnNtNjRod0Uzb1ByeU9QOHBibno5bklNeWZuY1BKR21kXzFnQXJPb3E3dFY5aXV2Q0o3NUo2b0ZvRGJSS2hOcEN5VGxwVmtsSkZ6Z0I4a3ZGelVKYjY3NA&q=http%3A%2F%2Fports.ubuntu.com%2Fubuntu-ports&v=7fSbzYsWD8Y) 
focal main restricted universe multiverse 
deb [arch=arm64] [http://ports.ubuntu.com/ubuntu-ports](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa1pvaUM5bVBFMWFGcm14eXM2dEo1LUpVTHIwZ3xBQ3Jtc0tsbjdHUmxXZk1JdFBsdDluOVloNXNWV1I2elBtSGs3anpXOFdPcVF1UkhObl95LU54UHFFQ3Fwc01KT1ZnLWZCeFFOMnB3RGtUYTV2c2EwbkN4Y2prWHBBMjBFaUMwNGxTRDAycWoxWFNOYmVkRURpSQ&q=http%3A%2F%2Fports.ubuntu.com%2Fubuntu-ports&v=7fSbzYsWD8Y) 
focal-updates main restricted universe multiverse 
deb [arch=arm64] [http://ports.ubuntu.com/ubuntu-ports](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbF9sN240WlI1TExPcUIwVUItRjJncnFZM3dnQXxBQ3Jtc0tubWxrQ2F5RE1ZeFNuajdDc0NnTld3SWxTeVNXVThCcVJTbk5DU3UwZTRjSjIzYkFBS3VaSW5ibGk1LWhzamlJOVNoSU1MVjR1RXZFNl81ZVFYQ1BIVFBsREw1NWctQTU0dVBmVXJSLTZKZHVYZ0tKMA&q=http%3A%2F%2Fports.ubuntu.com%2Fubuntu-ports&v=7fSbzYsWD8Y) 
focal-security main restricted universe multiverse 
deb [arch=i386,amd64] [http://us.archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa21obGs4bDlUR25SNmJ1NWU4ellFVWNveTVPd3xBQ3Jtc0tsTUZ4T2Nkc2dGM2pRWVJGaG9HcUxaYWY5eDhicW1mUkdsWjhuN1BPRi1TcWxJY3hpRHc4US1VVmpzN2pQU3ZWZGVWcXVvUFZxZVNHanNnUXRtVkRjdTk3LXl6MUtaRS0zVl9zQnJUdDJYZklCckVLVQ&q=http%3A%2F%2Fus.archive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal main restricted universe multiverse 
deb [arch=i386,amd64] [http://us.archive.ubuntu.com/ubuntu/](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbTk0YVlyX3BtWTdQN2tIRDZGcHpPTUNhbFFaQXxBQ3Jtc0tsazhvQ1pJamZRX0Nva1dsSXhSX3VhbjF2MkRCWEJYdHNqM2xhcTdSRFZzWnI4VGctOWVvcExjbXVTUTdYWFBBaFAtd0dobVAxRm45NzYyeWxuYWhLNTVIUFM3NWFLSHM1Y1RsLWxncTNvRVhYWkRmOA&q=http%3A%2F%2Fus.archive.ubuntu.com%2Fubuntu%2F&v=7fSbzYsWD8Y) 
focal-updates main restricted universe multiverse 
deb [arch=i386,amd64] [http://security.ubuntu.com/ubuntu](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa3l1cFNCMzRFQlRFelFzMm1wQW52MnYxQmlzQXxBQ3Jtc0ttb1ZWSEQtUUxzb2hkVjBpcjhfV1V0LXJyTEVBdTg2V3RLSkNudnZHa3lpOWkzSndfQlpvdFRwY19iVFk4N05qVkhjVVEwb0xtYzZRbHdYWTFXeGdxdVdDTHBRaEN4N3RsMGJLYWFXQ01FRGNQUkJsNA&q=http%3A%2F%2Fsecurity.ubuntu.com%2Fubuntu&v=7fSbzYsWD8Y) 
focal-security main restricted universe multiverse 

4. Add the specified public keys 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B4FE6ACC0B21F32 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 871920D1991BC93C 
5. Update 
sudo apt update 

6. Now install snort 
sudo apt install snort