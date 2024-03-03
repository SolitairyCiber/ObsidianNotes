**Also after a hack you want to see who has admin rights.  

```powershell
Connect-MsolService
```

```powershell
Get-MsolRoleMember -RoleObjectId $(Get-MsolRole -RoleName "Company Administrator").ObjectId
```
