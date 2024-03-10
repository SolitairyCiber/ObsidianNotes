```Powershell
Get-NetTCPConnection -state listen | Select-Object -Property *
```

or 

```PowerShell
Get-NetTCPConnection -state established | Select-Object -Property *
```



