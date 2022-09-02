Windows version info.
`SOFTWARE\Microsoft\Windows NT\CurrentVersion`

The hives containing the machine’s configuration data used for controlling system startup are called Control Sets.

`SYSTEM\ControlSet001`
`SYSTEM\ControlSet002`

Control set 2 is normally the last known good configuration. 

Windows creates a volatile Control Set when the machine is live, called the CurrentControlSet.

`HKLM\SYSTEM\CurrentControlSet`

For getting the most accurate system information, this is the hive that we will refer to. We can find out which Control Set is being used as the CurrentControlSet by looking at the following registry value:

`SYSTEM\Select\Current`

Last know good can be found here.

`SYSTEM\Select\LastKnownGood`

It is crucial to establish the Computer Name while performing forensic analysis to ensure that we are working on the machine we are supposed to work on. We can find the Computer Name from the following location:

`SYSTEM\CurrentControlSet\Control\ComputerName\ComputerName`


For accuracy, it is important to establish what time zone the computer is located in. This will help us understand the chronology of the events as they happened. For finding the Time Zone Information, we can look at the following location:

`SYSTEM\CurrentControlSet\Control\TimeZoneInformation`

The following registry key will give a list of network interfaces on the machine we are investigating:

`SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces`


The past networks a given machine was connected to can be found in the following locations:

`SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Unmanaged`

`SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList\Signatures\Managed`

The following registry keys include information about programs or commands that run when a user logs on.

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\Run`

`NTUSER.DAT\Software\Microsoft\Windows\CurrentVersion\RunOnce`

`SOFTWARE\Microsoft\Windows\CurrentVersion\RunOnce`

`SOFTWARE\Microsoft\Windows\CurrentVersion\policies\Explorer\Run`

`SOFTWARE\Microsoft\Windows\CurrentVersion\Run`


Services registry keys.

`SYSTEM\CurrentControlSet\Services`

The SAM hive contains user account information, login information, and group information. This information is mainly located in the following location:

`SAM\Domains\Account\Users`

