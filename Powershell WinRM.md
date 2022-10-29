On remote machine.
>get-service winrm

If service is not running.
>Enable-PSRemoting

Open firewall ports if necessary.
> Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP" -RemoteAddress Any
> Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-NoScope" -RemoteAddress Any

If not joined to a domain then use this firewall rule.
> Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any

Test the connection to the remote machine.
> Test-WSMan server1

**Hint**. If you are connecting to a remote computer via PS Remoting by an IP address, you may receive an error:

Connecting to remote server 192.168.1.70 failed with the following error message: The WinRM client cannot process the request. Default authentication may be used with an IP address under the following conditions: the transport is HTTPS or the destination is in the TrustedHosts list, and explicit credentials are provided.

In this case, you need to install an HTTPS certificate for PowerShell Remoting on the remote computer (the long way), or add this host to the trusted ones on your management computer:

> Set-Item wsman:\localhost\Client\TrustedHosts -value 192.168.1.70
    Restart-Service WinRM

Now create a remote session.

> Enter-PSSession -ComputerName 10.0.2.33 -Credential $Credentials

To exit.

> Exit-PSSession


