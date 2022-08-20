SMTP enable or disable

Tenent wide

>Get-TransportConfig | Format-List SmtpClientAuthenticationDisabled

>Set-TransportConfig -SmtpClientAuthenticationDisabled $true or $false

User Mailbox

>Set-CASMailbox -Identity <MailboxIdentity> -SmtpClientAuthenticationDisabled <$true | $false | $null>

>Get-CASMailbox -Identity <MailboxIdentity>  | Format-List SmtpClientAuthenticationDisabled


