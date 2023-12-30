Download dumpit from github
Simple to use just run the exe and say yes to dump ram to a file.

Ftk imager is an alternative GUI tool that does the same thing.

Move memory dump file to a clean machine and download volatility or volatility workbench for the GUI version. 

Using the GUI workbench version click on get process list and it will list all the processes.
Look for suspicious processes.

Next run the Malfind.
This will look for process injection and other malware behavior.  

The command line tool has more options so to find connected IP ports.
vol.exe -f filename.mdp windows.netstat

If there are suspicious IP addresses you can find out more at:
whatsmyipaddress.com

A more automated analysis upload the dump file to:
analyze.intezer.com
There is also a stand alone tool called Endpoint you can download and run with intezer that will allow you to analize from the infected machine.  