List applications.
``` powershell
Get-WmiObject -Class Win32_Product | Select-Object -Property Name
```

Assign variable to application. Example here is wolf security. 
``` powershell
$MyApp = Get-WmiObject -Class Win32_Product | Where-Object{$_.Name -eq "HP Wolf Security"}
```

Uninstall application.
``` powershell
$MyApp.Uninstall()
```