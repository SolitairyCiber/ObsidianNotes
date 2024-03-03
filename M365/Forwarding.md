**After a hack you will want to check what email is being forwarded.  
View forwarding email.

```PowerShell
Get-Mailbox | select UserPrincipalName,ForwardingSmtpAddress,DeliverToMailboxAndForward
```

**Stop forwarding email.

```PowerShell
Set-Mailbox paulie -ForwardingAddress $NULL -ForwardingSmtpAddress $NULL
```

