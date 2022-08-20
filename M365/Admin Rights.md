Also after a hack you want to see who has admin rights.  

>Connect-MsolService

>Get-MsolRoleMember -RoleObjectId $(Get-MsolRole -RoleName "Company Administrator").ObjectId