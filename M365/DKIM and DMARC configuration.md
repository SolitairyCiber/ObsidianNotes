### DKIM
In 365 go to admin then under Admin Centers choose Security
Email and Collaboration
Policies & Rules
Threat Policies
Under Rules look for Email Authentication Settings.
Click on DKIM at top.
Choose the correct domain.
Click on create dkim
Then copy and paste into notepad

I had some issue with this so powershell was used.
``` powershell
Connect-ExchangeOnline
Get-DkimSigningConfig
Set-DkimSigningConfig -Identity <domain name> -Enabled $true
# to check they keys

Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

#### Now in DNS
Create a CNAME record for selector1.\_domainkey with the info given above.
Now do the same for selector2

Now back in 365 click on the disable button to enable it.

### DMARC
Now you can create your DMARC TXT record.
\_DMARC.domainname.com "v=DMARC1; p=quarantine; pct=100"