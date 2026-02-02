
Check to see if it is enabled.

```powershell 
Get-CasMailbox | Select-Object PrimarySmtpAddress, ImapEnabled, PopEnabled
```

Disable IMAP and POP.
```powershell
Get-CasMailbox -ResultSize Unlimited | Set-CasMailbox -ImapEnabled $false -PopEnabled $false
```

