
Find network adapter name.
``` 
networkctl
```

Next start the adapter.
``` 
 ip link set up YOUR_NIC
```

Now configure the IP address.
```
netplan set ethernets.enp0s2.addresses=[10.0.2.15/24]
```

Now change the netplan file.
```
nano /etc/netplan/01-netcfg.yaml
```
It might be something besides 01.

Now edit the file.
```
ethernets:
        enp3s0:
            addresses:
                - 10.10.10.2/24
            nameservers:
                addresses: [10.10.10.1, 1.1.1.1]
            routes:
                - to: default
                  via: 10.10.10.1
```

Note that the indents have to be exactly the same.  

Now apply.
```
netplan apply
```