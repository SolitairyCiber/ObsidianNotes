After a hack you will want to check what email is being forwarded.  
View forwarding email.

>Get-Mailbox | select UserPrincipalName,ForwardingSmtpAddress,DeliverToMailboxAndForward

Stop forwarding email.

>Set-Mailbox paulie -ForwardingAddress $NULL -ForwardingSmtpAddress $NULL

