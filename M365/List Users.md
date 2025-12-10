```PowerShell
Get-Recipient | Select DisplayName, Name, RecipientType, EmailAddresses
```

``` powershell
Get-Recipient -ResultSize Unlimited | Select-Object DisplayName, @{Name="SMTP Addresses";Expression={($_.EmailAddresses | Where-Object { $_ -match "^smtp:" } | ForEach-Object {$_ -replace "smtp:",""}) -join ";" }}
```

Get name from GUID

```powershell
Get-EXOMailbox -Identity <MailboxGUID> | Select-Object DisplayName, UserPrincipalName, SamAccountName
```