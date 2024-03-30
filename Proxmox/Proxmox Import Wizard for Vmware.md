Must be on version 8.1.3 or newer.
1. In Proxmox click on you server then updates then repositories.
2. Disable the enterprise repositories if you don't have the paid version.
3. Click ADD then with the drop down box add the no subscription repository.
4. Repeat the ADD button and choose the Ceph Reef No Subscription repository.
5. Go back up to updates.
6. Click the refresh button.  
7. The click the upgrade button to get the latest updates.
8. Reboot the Proxmox host.
9. SSH into the host.
10. run apt install pve-esxi-import-tools -y
11. It probably is already installed but this is a check to be sure.
12. Now we add the esxi datastore to the Proxmox host.
13. Go to the datacenter top level in Proxmox.
14. Choose ADD then esxi.
15. Give it a name and fill in the IP and login info.
16. Also check the skip verification step button because we normally don't put a SSL certificate on our esxi servers.
17. Now when you click on the esxi datastore you should see the folders.
18. Now go to esxi and power off the machine you want to migrate.
19. Back in Proxmox when you click on the VM folder you will see the import button is able to be clicked.
20. You can fill in the form.  It typically lets you set things like number of CPUs and RAM.  You might want to change the controller to virt-iscsi.  
21. An important note is there is a "live import" option.  This does not mean what you would intuitively think it does.  What it means is as soon as enough has been imported to power up it will.  Now I don't see this as a vary viable option but try it if you like.  
22. Boot up the migrated virtual machine and you are done.  
