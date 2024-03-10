**Also after a hack looking at client side rules are important.  

**This gets client side rules and their names.

```PowerShell
Get-InboxRule –Mailbox <mailbox_user> | Select Name, Description | FL
```

**This one gives more detailed info.

```PowerShell
Get-InboxRule -Mailbox Joe@Contoso.com
```

**If you want to export the rules to a csv for review use this. 

```Powershell 
Get-Mailbox | select UserPrincipalName,ForwardingSmtpAddress,DeliverToMailboxAndForward | Export-csv D:\Office365Forwards.csv -NoTypeInformation
```


**Get forwarding of all forwarding rules not just to outside enties.

```PowerShell
$mailboxes=(get-mailbox).UserPrincipalName;foreach ($mailbox in $mailboxes) {get-inboxrule -Mailbox $mailbox | Select Identity, Name, Description, ForwardTo | FL} 
```

***Get mailbox object ID

```PowerShell
get-mailbox <username> |select ExternalDirectoryObjectId
```

**Stop forwarding rule.

```PowerShell
Remove-InboxRule -Mailbox 84580631-c4d9-415d-8dd5-c78be65e433f -Identity "Send me a copy" 
```

**I ran into a case where they used the same name for the rule and the above would not remove it.  In that case to remove all rules.

```PowerShell
Get-InboxRule -Mailbox "cameron@ohdbc.com" | Remove-InboxRule
```



