**SMTP enable or disable

**Tennent wide

```PowerShell
Get-TransportConfig | Format-List SmtpClientAuthenticationDisabled

Set-TransportConfig -SmtpClientAuthenticationDisabled $true or $false
```

**User Mailbox

```PowerShell

Set-CASMailbox -Identity <MailboxIdentity> -SmtpClientAuthenticationDisabled <$true | $false | $null>

Get-CASMailbox -Identity <MailboxIdentity>  | Format-List SmtpClientAuthenticationDisabled
```


