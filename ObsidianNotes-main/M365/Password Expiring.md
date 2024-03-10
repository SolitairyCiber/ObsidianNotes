
**You might not want the admin password to expire

**View the status of a user.

```PowerShell
Get-MsolUser -UserPrincipalName <fullemailaddress@yourdomain.com> | Select PasswordNeverExpires
```

**Change the status of a user expiring status.

```PowerShell
Connect-MsolService
Set-MsolUser -UserPrincipalName <fullemailaddress@yourdomain.com> -PasswordNeverExpires $true
```

