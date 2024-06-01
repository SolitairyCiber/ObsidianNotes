esxcfg-info | less
vmware -vl
esxcfg-nics -l
esxcfg-switch -l
esxtop d (storage view)
tail -f /var/log/vmkernel.log

reboot -n -f

finds all snapshots:
find -iname *delta* | less

checks logs
tail /var/log/vmkwarning.log

vim-cmd vmsvc/getallvms