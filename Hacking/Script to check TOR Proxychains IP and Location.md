```
#!/bin/bash
torip=$(proxychains4 curl whatismyipaddress.com | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" | head -n 1)
curl ipinfo.io/$torip

```