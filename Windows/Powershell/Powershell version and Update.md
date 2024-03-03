```powershell
Get-Host | Select-Object Version
```

To upgrade your PowerShell version to 5.1, install the **Windows Management Framework 5.1**, which requires the **.NET Framework 4.5.2** (or newer). Make sure that .NET 4.5.2 or higher is installed using this command:

```PowerShell
(Get-ItemProperty ‘HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full’ -Name Release).Release
```

Offline installer if update is required.  [https://go.microsoft.com/fwlink/?linkid=2088631](https://go.microsoft.com/fwlink/?linkid=2088631)


```Shell
msiexec.exe /package PowerShell-7.1.0-win-x86.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```







