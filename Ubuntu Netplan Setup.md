
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

