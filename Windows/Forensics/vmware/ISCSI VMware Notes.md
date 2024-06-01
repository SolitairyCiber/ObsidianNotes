
**I know these are not step by step but I will attempt to improve them next time I do one.  

create a virtual switch
ISCSI-SW
add both NICs.

create two port groups
choose ISCSI-SW
Override nic teaming
Mark one NIC in each port group as unused.

Add two vmkernel nics with static IP addresses

Now go to storage and add ISCSI adapter.
Add the two vmkernel nics
add the IP addresses of the san in dynamic targets

Then go back to the san and you should be able to add the host as the initator will show up now.

Now go back to the host and add static addresses.  The name should fill in after some time.

