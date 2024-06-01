Make sure DNS is correct on DNS server as well as pointer records.

check /etc/host
127.0.0.1 vcenter.domain.com

```Shell
/opt/vmware/share/vami/vami_config_net 
```

0 to show config
then pick the number to fix any issues. make sure DNS points to correct server.  

Check that time and date are accurate.

To check the certificates to see they expired.

```Shell
for i in $(/usr/lib/vmware-vmafd/bin/vecs-cli store list); do echo STORE $i; sudo /usr/lib/vmware-vmafd/bin/vecs-cli entry list --store $i --text | egrep "Alias|Not After"; done
```

If certificates are expired.
```Shell
/usr/lib/vmware-vmca/bin/certificate-manager
```

4 to replace all certificates.
Or pick the number for the certificate you need to update.  