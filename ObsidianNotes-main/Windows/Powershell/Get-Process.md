```powershell
Get-Process -Name winlogon


(Get-Process -Name '*').Path

$cpu=(Get-Process -Name 'whateverthenameis').CPU
"[math]::Round($cpu,2)"

#Remove quotes from above math when using.  


#Requires elevated privilages

Get-Process -Name 'Calculator' -IncludeUserName


#Intresting for checking processes on remote computers

Get-Process -ComputerName 'remote_computer_name' -ProcessName 'process'

```

