On workstation you want to access.
```powershell
Enable PSRemoting
Get-Item wsman:\localhost\client\trustedhosts
Set-Item wsman:\localhost\client\trustedhosts -Value "dc1.xyz.com"
# IP address can also be used and must be if workstation is not in domain.
```

Now on the server you wish to use to access the workstation.

```powershell
#test with
Invoke-Command -Computer "workstation" -ScriptBlock { whoami }

# Open a session
Enter-PSSession workstation 

```