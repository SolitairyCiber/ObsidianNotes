If a person needs access to another users mailbox this is the spot.
This will list the permissions on a mailbox.

>Get-MailboxPermission username | Format-Table -Wrap -AutoSize

This will give a user permissions.

>Add-MailboxPermission -Identity usernam -User useryouwanttohaveright@domain.com -AccessRights FullAccess -InheritanceType All

This will remove rights and must be done before you can change them if the user has wrong permissions. 

>Remove-MailboxPermission  <Identity>  -User <Identity>  -AccessRights FullAccess

If for some reason you don't want the mailbox to automatically show up you can turn off automapping.


>Add-MailboxPermission -Identity johnsmith@contoso.onmicrosoft.com -User admin@contoso.onmicrosoft.com -AccessRights FullAccess -AutoMapping $false

