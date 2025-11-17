
Open Powershell as admin.
Install module.
```powershell
Import-Module Microsoft.PowerShell.Management
```

You may need to restart powershell after the above command.

Now lets test it.

```powershell
Test-ComputerSecureChannel
```

If this returns false then the relationship is broken.

Let's fix it.

```powershell
$credential = Get-Credential
Test-ComputerSecureChannel -Repair -Credential $credential
```

Next do this.

```powershell
$credential = Get-Credential
Reset-ComputerMachinePassword -Server [DomainControllerName] -Credential $credential
```