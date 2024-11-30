After after burning to the SD card open in a Linux VM as Windows can't see the main partition.

Edit **/boot/config.txt** by appending the following line to the end of the file:

``` 
dtoverlay=dwc2
```

Edit **/boot/cmdline.txt** by inserting the following text between **rootwait** and **quiet**

Note that quiet may not be there so just after rootwait.

```
modules-load=dwc2,g_ether g_ether.dev_addr=12:34:56:78:9a:bc g_ether.host_addr=16:23:45:78:9a:bc
```

Create a new udev rule file. Create **/etc/udev/rules.d/90-usb-gadget.rules** and insert the following:

```
SUBSYSTEM=="net",ACTION=="add",KERNEL=="usb0",RUN+="/sbin/ifconfig usb0 192.168.1.2 netmask 255.255.255.0",RUN+="/usr/bin/python -c 'import time; time.sleep(20)'",RUN+="/sbin/ip route add 192.168.1.1 dev usb0"
```

Edit **/etc/sysctl.conf** and append the following line to the end of the file (this allows **normal mode**, when not a gadget):

```
net.ipv4.conf.all.ignore_routes_with_linkdown=1
```

That is all you need to do in the SD card.

Now prepare windows.  Plug in the Pi to the windows USB port.

 Download [mod-duo-rndis.zip](https://github.com/charkster/rpi_gadget_mode/blob/main/mod-duo-rndis.zip) and unzip

Then update the COM port driver that it is identified as.  Now you should have a gadget in the Control Panel\Network and Internet\Network Connections.
Change the IP address.  This can be whatever was set by the Linux distro.  But the convention seems to be that the distro ends in dot 2.  With Kali it is 192.168.1.1 you will need to put on your PC but I have also seen 172.20.10.1 for pawnagochi.  Now you can access the Pi via SSH and run vncserver on the PI to get to the GUI.  From there you can set the WiFi and connect normally or keep accessing via gadget mode.  