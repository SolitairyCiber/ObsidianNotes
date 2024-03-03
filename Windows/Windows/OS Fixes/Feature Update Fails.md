Open a Command Prompt window (cmd) as admin.

To check the WinRE status, run reagentc /info. If the WinRE is installed, there should be a "Windows RE location" with a path to the WinRE directory. An example is, "Windows RE location: [file://%3f/GLOBALROOT/device/harddisk0/partition4/Recovery/WindowsRE]\\?\GLOBALROOT\device\harddisk0\partition4\Recovery\WindowsRE." Here, the number after "harddisk" and "partition" is the index of the disk and partition WinRE is on.

To disable the WinRE, run reagentc /disable

Shrink the OS partition and prepare the disk for a new recovery partition.

To shrink the OS, run diskpart

Run list disk

To select the OS disk, run sel disk<OS disk index>  This should be the same disk index as WinRE.

To check the partition under the OS disk and find the OS partition, run list part

To select the OS partition, run sel part<OS partition index>

Run shrink desired=250 minimum=250

To select the WinRE partition, run sel part<WinRE partition index>

To delete the WinRE partition, run delete partition override

Create a new recovery partition.

First, check if the disk partition style is a GUID Partition Table (GPT) or a Master Boot Record (MBR).  To do that, run list disk. Check if there is an asterisk character (*) in the "Gpt" column.  If there is an asterisk character (*), then the drive is GPT. Otherwise, the drive is MBR.

If your disk is GPT, run create partition primary id=de94bba4-06d1-4d40-a16a-bfd50179d6ac followed by the command gpt attributes =0x8000000000000001

If your disk is MBR, run create partition primary id=27

To format the partition, run format quick fs=ntfs label="Windows RE tools"

To confirm that the WinRE partition is created, run list vol

To exit from diskpart, run exit

To re-enable WinRE, run reagentc /enable

To confirm where WinRE is installed, run reagentc /info

After completing these steps, reboot Windows and check for updates in Windows Update to try and install the KB5034441 security update again.