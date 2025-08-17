Let's list the volumes available.
```
lsblk
```

Let's say the disk we want to mount is sdb.  Next we need to prepare the disk. First step is to create the partition.
```
fdisk /dev/sdb
```

Create a new partition.
```
n
```

Make it a primary.
```
p
```

Accept all defaults.  Then write it.
```
w
```

Now we format the partition.  
```
mkfs.ext4 /dev/sdb1
```

Now we need the block ID.  We do this because using the /dev may change it we add drives or plug into a different USB port.
```
blkid /dev/sdb1
```

The number we are looking for is the UUID.  
Next we will need to find out what the systemd file needs to be named to mount it.  No need to create the directory systemd will do it for you.  So if we want to mount it at /mnt/disk_2.
```
systemd-escape -p --suffix=mount "/mnt/disk_2"
```

This will give you a file name to create.  Save it in a text file along with the UUID of the volume.

Now create the file. I our case the file name is.  
```
nano /etc/systemd/system/mnt-disk_2.mount
```

Here are some examples of what that file should look like. 

### mnt-disk_2.mount

```
[Unit]
Description=Mount storage volume

[Mount]
What=/dev/disk/by-uuid/e1d1a2dd-dbdd-41e1-bc54-00ff8fe4e6a0
Where=/mnt/disk_2
Type=ext4
Options=rw,noatime

[Install]
WantedBy=multi-user.target
```

### mnt-nfs_share.mount

```
[Unit]
Description = NFS mount

[Mount]
What=srv-nas-truenas-prod-1.learnlinux.tv:/mnt/volume2/public
Where=/mnt/nfs_share
Type=nfs
Options=defaults
TimeoutSec=5

[Install]
WantedBy=multi-user.target
```

### mnt-nfs_share.automount

```
[Unit]
Description=NFS Automount

[Automount]
Where=/mnt/nfs_share
TimeoutIdleSec=10

[Install]
WantedBy=multi-user.target
```

