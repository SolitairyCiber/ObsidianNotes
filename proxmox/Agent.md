Enable in Proxmox options for VM
Next install agent.
Linux
```
apt install qume-guest-agent 
```
Windows
download the driver
https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/archive-virtio/?C=M;O=D

Then install the virtio-serial driver:

1. Attach the ISO to your windows VM (virtio-*.iso)
2. Go to the windows Device Manager
3. Look for "PCI Simple Communications Controller"
4. Right Click -> Update Driver and select on the mounted iso in DRIVE:\vioserial\<OSVERSION>\ where <OSVERSION> is your Windows Version (e.g. 2k12R2 for Windows 2012 R2)

After that, you have to install the qemu-guest-agent:

1. Go to the mounted ISO in explorer
2. The guest agent installer is in the directory **guest-agent**
3. Execute the installer with double click (either **qemu-ga-x86_64.msi** (64-bit) or **qemu-ga-i386.msi** (32-bit)

After that the qemu-guest-agent should be up and running. You can validate this in the list of Window Services, or in a PowerShell with:

