password expiring
You might not want the admin password to expire

View the status of a user.

>Get-MsolUser -UserPrincipalName <fullemailaddress@yourdomain.com> | Select PasswordNeverExpires

Change the status of a user expiring status.

>Connect-MsolService
Set-MsolUser -UserPrincipalName <fullemailaddress@yourdomain.com> -PasswordNeverExpires $true
