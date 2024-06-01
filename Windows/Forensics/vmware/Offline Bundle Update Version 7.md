Get the profile list. Change the name of the file to the one you downloaded and the path to the datastore you downloaded it to.  
```Shell

esxcli software sources profile list --depot=/vmfs/volumes/<Datastore>/VMware-ESXi-6.7.0-17167734-HPE-Gen9plus-670.U3.10.6.3.8-Jan2021-depot.zip
```

Install the offline bundle you uploaded to the datastore. Replace the path and file like above and add the results above to the --profile= line.  
```Shell
esxcli software profile update --depot=/vmfs/volumes/<Datastore>/VMware-ESXi-6.7.0-17167734-HPE-Gen9plus-670.U3.10.6.3.8-Jan2021-depot.zip --profile=HPE-ESXi-6.7.0-Update3-Gen9plus-670.U3.10.6.3.8
```


