Deployed Printers Not Working

On workstations:

HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows NT\\Printers\\PointAndPrint

NoWarningNoElevationOnInstall = 0 (DWORD) or not defined (default setting) AND
UpdatePromptSettings = 0 (DWORD) or not defined (default setting)
RestrictDriverInstallationToAdministrators = 0 DWORD

Not sure if this one was necessary but I did it on the test pc so 

HKEY_LOCAL_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\wscsvc

DelayedAutoStart = 0 dword

Expand the following branch in the Group Policy editor: Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > Security Options. Find the policy Devices: Prevent users from installing printer drivers.

Set the policy value to Disable.

packaged point and print approved servers gpo emabled

Or just go back to v3 drivers.  