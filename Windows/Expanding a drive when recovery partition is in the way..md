
Here’s how to correctly move the Windows Recovery Partition on a Windows server or a normal Windows system.

This is what my partitions look like in Disk Management.

[![](https://thedxt.ca/wp-content/uploads/2023/06/diskmgmt-before.png)](https://thedxt.ca/wp-content/uploads/2023/06/diskmgmt-before.png)

We will move the 1 GB recovery partition to the end of the disk allowing us to add the 50 GB of unallocated space to the C drive.

# The Process

- Make sure you have a backup of the system you are going to edit the partitions on.
- Open Command Prompt as admin

![](https://thedxt.ca/wp-content/uploads/2023/06/CMD-Admin.png)

Run CMD as admin

## Disabling The Windows Recovery Partition

- We need to disable the existing Windows Recovery Partition to do that run the command `reagentc /disable`

![](https://thedxt.ca/wp-content/uploads/2023/06/reagentc-disable.png)

Disabling the Recovery Partition

The `reagentc /disable` command will disable the recovery partition and will move the recovery partition into a file named `Winre.wim` and will be located in `C:\Windows\System32\Recovery` (you have to enable showing hidden system files if you want to see it)

![](https://thedxt.ca/wp-content/uploads/2023/06/disabled-windows-RE.png)

The Windows Recovery Partition File

## DiskPart

- Run the command `diskpart` to launch DiskPart

![](https://thedxt.ca/wp-content/uploads/2023/06/diskpart.png)

Launching DiskPart

- List the disks in your system. You can do this by using the command `list disk`

![](https://thedxt.ca/wp-content/uploads/2023/06/list-disk.png)

Listing the disks in DiskPart and showing the disk is a GPT disk

Pro tip from Matt in the comments, if there’s a * in the column for Gpt that means the disk is likely a GPT disk and if there isn’t a * in the Gpt column the disk is likely MBR. Make a note of this as it will be important further down.

- Select the disk you need to move the recovery partition on. You can do this by using the command `select disk` and the disk number. In my setup disk 0 was the correct disk and the command I entered was `select disk 0`.

![](https://thedxt.ca/wp-content/uploads/2023/06/sel-disk.png)

Selecting the disk in DiskPart

- List the partitions on that disk. You can do this by using the command `list partition`

![](https://thedxt.ca/wp-content/uploads/2023/06/list-par.png)

Listing the partitions in DiskPart

- Select the recovery partition. You can do this by using the command `select partition` and the partition number. In my setup partition 4 is my recovery partition and the command I entered was `select partition 4`

![](https://thedxt.ca/wp-content/uploads/2023/06/sel-par.png)

Selecting the partition in DiskPart

The recovery partition is a protected partition so we need to use a bit more force to delete it.

- Force the deletion of the recovery partition. You can do this by using the command `delete partition override`

![](https://thedxt.ca/wp-content/uploads/2023/06/del-par-force.png)

Forcing the partition deletion

## Disk Management

Now if you look in Disk Management you should no longer have the Recovery Partition and it should show up as unallocated.

![](https://thedxt.ca/wp-content/uploads/2023/06/deleted-Windows-RE.png)

Disk Management with the Recovery Partition deleted

- Expand your disk and leave about 1024 MB off your resized size to leave room for the re-enabling the Recovery Partition.

![](https://thedxt.ca/wp-content/uploads/2023/06/Extend-Disk.png)

Expanding the partition but leaving room for the Windows Recovery Partition

Disk Management should now look something like this.

![](https://thedxt.ca/wp-content/uploads/2023/06/resized-disk.png)

Disk Management after expanding the disk and leaving room for the Windows Recovery Partition

Once the disk is expanded we need to rebuild everything that is needed for Windows to know that the extra space that we left unallocated can be used to for the recovery partition.

- Create a New Simple Volume with the unallocated space.

![](https://thedxt.ca/wp-content/uploads/2023/06/new-simple-vol.png)

Creating a New Simple Volume

- Don’t give it a drive letter.

![](https://thedxt.ca/wp-content/uploads/2023/06/no-dirve-letter.png)

Not giving the New Simple Volume a drive letter or a drive path

- You can give the new partition a name if you want it does not mater. I’m going to call mine New Recovery.

![](https://thedxt.ca/wp-content/uploads/2023/06/partition-name.png)

Naming the New Simple Volume

Disk Management should now look something like this.

![](https://thedxt.ca/wp-content/uploads/2023/06/diskmgmt-new-par.png)

Disk Management with the newly created partition that will become the Windows Recovery Partition

## Back to DiskPart

- In DiskPart list your partitions again by running the command `list partition`

![](https://thedxt.ca/wp-content/uploads/2023/06/list-par-2nd-time.png)

Listing the partitions with DiskPart

- Select the 1024 MB partition with the command `select partition` and the partition number. In my setup it was partition 4 and the command I ran was `select partition 4`

![](https://thedxt.ca/wp-content/uploads/2023/06/sel-par.png)

Selecting the partition with DiskPart

If you have a GPT disk you need to run some very specific command and if you have an MBR disk you need to run different very specific commands.

### GPT disk

On GPT disks we need to change the partition ID to **de94bba4-06d1-4d40-a16a-bfd50179d6ac** which tells Windows that this is a recovery partition

- Run the following command to set the partition as a recovery partition `set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac`

![](https://thedxt.ca/wp-content/uploads/2023/06/GPT-par-ID.png)

Setting the GPT partition ID in DiskPart

We also need to hide the drive and flag it as a required partition to do that we have to set a GPT attribute to **0x8000000000000001**

- Run the following command to set the GPT attribute to hide the drive and flag it as required `gpt attributes=0x8000000000000001`

![](https://thedxt.ca/wp-content/uploads/2023/06/gpt-attribute.png)

Setting the GPT attribute in DiskPart

- Now we can exist DiskPart.

![](https://thedxt.ca/wp-content/uploads/2023/06/exit-diskpart.png)

Exiting DiskPart

### MBR disk

On MBR disks we need to change partition ID to **27** which will tell Windows that this is a recovery partition.

- Run the following command to set the partition as a recovery partition `set id=27`

![](https://thedxt.ca/wp-content/uploads/2023/06/BIOS-par-ID.png)

setting the MBR partition ID in DiskPart

- Now we can exist DiskPart.

![](https://thedxt.ca/wp-content/uploads/2023/06/exit-diskpart.png)

Exiting DiskPart

## Enabling The Windows Recovery Partition

- Now we can re-enable the recovery partition by running the command `reagentc /enable`

![](https://thedxt.ca/wp-content/uploads/2023/06/reagentc-enable.png)

Enabling the Windows Recovery Partition

The `reagentc /enable` command will copy the `Winre.wim` file from `C:\Windows\System32\Recovery` into our new recovery partition.

![](https://thedxt.ca/wp-content/uploads/2023/06/enabled-windows-RE.png)

Windows Recovery Partition file is now back on the recovery partition

If you look at Disk Management again everything shows up correctly.

![](https://thedxt.ca/wp-content/uploads/2023/06/moved-Windows-RE.png)

That’s all there is to it.