**This Worked Best 

Download the ova file and extract the components.
Unzip the vmdk file.
SCP vmdk file to proxmox server.
Create a new vm.  ISCSI drive and VMware compatible video driver.
Create the drive on a datastore not local.
Delete the qcow2 drive.
Next run this.
 qm importdisk 103 remnux-v7-focal-disk1.vmdk local -format qcow2
 Where 103 is the ID of the vm.
ifconfig ens18 ipaddress
ifconfig ens18 up
route add default gw {IP-ADDRESS} {INTERFACE-NAME}
nano /etc/resolv.conf




**Alternate Technique**  

Download the Ubuntu mini iso.  This is hard to find as most web links are dead.  So try here.
http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/

Upload to Proxmox and create a new vm.
Settings make sure to use ISCSI for the disk.

Boot the iso and set the following
Full Username REMnux user
login remnux
password malware

Once base install is complete and don't install any components run the following.

wget https://REMnux.org/remnux-cli
mv remnux-cli remnux
chmod +x remnux
sudo mv remnux /usr/local/bin
sudo apt install -y gnupg curl
sudo remnux install
or
sudo remnux install --mode=cloud
if you want to have ssh


may have to set these too
1. VM > Hardware > Display > Set to -> SPICE(qxl) or what worked for me was VMware compatible
2. VM > Hardware > Option > Spice Enhancements > Video Streaming: all