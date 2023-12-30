Run something.
> ```powershell
> Start-Process Notepad.exe
> ```

Show running processes. Leave off -name if you want to see them all.
> ```powershell
> Get-process -name Notepad.exe
> ```

Wanna keep a CSV file of any results then pipe it through the CSV gnerator?
> ```powershell
> | Export-CSV filename.csv
> ```

Read a file from the command line like cat in Linux?

>```powershell
>Get-Content filename.txt
>```


Copy and Move commands.
> ```powershell
> Copy-Item 
> Move-Item
> ```

Want to submit a hash to virtustotal or some other reason?
>```powershell
>Get-FileHash -algorithm SHA256 filename.xxx
>```


File download.
Just a reminder on creating web server with python.
> python -m http.server 7331

Now to download.

>```powershell
(NewObject System.Net.WebClient) .downloadfile('http://xxx.xxx.xxx.xxx/myfile.xxx' 'myfile.xxx')


Or you can use.

> ```powershell
> Invoke-WebRequest "http://xxx.xxx.xxx.xxx/file.xxx" -outfile "file.xxx"


Execution Policy.
> ```powershell
Get-ExecutionPolicy -list
> Set-ExecutionPolicy unrestricted

List Windows updates.
>```powershell
Get-HotFix

Format the list.
> ```powershell
Get-HotFix | Format-List | findstr InstalledOn

Looking at files more closley.
> ```powershell
dir | Format-List *
> 

Pipe anything through outfile gives you a file to view later.
>```powershell
 | Out-File file.xxx

Lets see what is alive on the network.
>```powershell
1..15 | ${echo "10.0.0.$_": ping -n 1 10.0.0.$_ _  | Select-String ttl} 

Powerview script.
[https://github.com/PowerShellMafia/PowerSploit/blob/dev/Recon/PowerView.ps1](https://github.com/PowerShellMafia/PowerSploit/blob/dev/Recon/PowerView.ps1)

> ```powershell
Import-Module .\powerview.ps1

Now we can use the powerview commands.

> Get-NetDomainController
> Get-NetUser
> Get-NetUser | select -ExpandProperty lastlogon
> Get-NetComputer
> Get-NetGroup
> Get-NetGroupMember
> Find-DomainShare
> Get-NetGPO
> 

