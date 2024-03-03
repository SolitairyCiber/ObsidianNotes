set the BBWC/FBWC to 50%/50% read/write int the ACU
ensure "Power Management" is set to "Static High" in the BIOS
check whether the partitions in the Windows 2003 are properly aligned to 1024kB (instead of 31.5kB by default)
lower the vCPU count for the VMs to half of what it is currently (at least temporarily to test performance)
optional: in case this is a DL380 enable the "Execute Disable Bit (XD)" in the BIOS, in case it's an AMD host (DL385) enable "NX"
