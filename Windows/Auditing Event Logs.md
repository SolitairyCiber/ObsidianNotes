# This gets the failed longin attemps.  

~~~ powershell
Get-eventlog -logname security | where-object {$_eventid -eq 4625}
~~~
powershell events
4103
4104
4688

powershell logs

gpo
computer/policies/admin templates/windows components/windows powershell
turn on module logging 
turn on poershell script events seclect log cript block invocation start/stop events

4688
copmuter/polocies/windows settings/security settings/advanced audit configuration/detailed tracking/
audit process creation success&failure

computer/polocies/administrative templates/system/aduit prcess creation
include command line events


Get-EventLog -LogName System -EntryType Error

Get-EventLog -LogName System -InstanceID 3221235481 -Source "DCOM"

Get-EventLog -LogName "Windows PowerShell" -ComputerName "localhost", "Server01", "Server02"

Get-EventLog -LogName "Windows PowerShell" -Message "*failed*"

$A = Get-EventLog -Log System -Newest 1
$A | Format-List -Property *