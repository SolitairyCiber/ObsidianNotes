Let's list the volumes available.
```
lsblk
```

Let's say the disk we want to mount is sdb.  Next we need to prepare the disk. First step is to create the partition.
```
fdisk /dev/sdb
n #creates new parition
p # creates primary partition

```
