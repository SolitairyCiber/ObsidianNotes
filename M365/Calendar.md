**Find out who has permission to a calendar.
```PowerShell
Get-MailboxFolderPermission username:\calendar
```

**Now lets give a user permission to another users calendar.
This example gives user2 editor permissions to user1 calendar
```PowerShell
Add-MailboxFolderPermission -Identity user1@domain.com:\calendar -user user2@domain.com -AccessRights Editor
```

**If permissions are already there you must first remove them.
```PowerShell
Remove-MailboxFolderPermission -Identity user1@domain.com:\calendar –user user2@domain.com
```

**If you want to give all users permissions to a calendar use this.  
```PowerShell
Set-MailboxFolderPermission -Identity user1@domain.com:\calendar -User Default -AccessRights Reviewer
```


