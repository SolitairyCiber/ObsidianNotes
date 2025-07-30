If you can't log in at all you need to enable the admin account.
You must boot off an ISO image and get into windows recovery.  It will not work just to go into recovery mode you have to boot off the ISO.
Use diskpart to assign a drive letter if your C drive is not visable.
Type regedit
Click on local machine. 
Click File then Load Hive
Browse to c:\windows\system32\config and choose the SAM file.
You can name it whatever you like.  I use temp,
Now go to Temp\SAM\Account\
Pick the one that ends in 1f4 normally 000001f4 and normally the top one.
Open the f value which is a binary value.
Go down to the 8th row first column.  
The value should be 11 and you want to delete that and change it to 10.
Note you must delete the 11 if you try to copy over it it will shift not copy over.
Unload the hive don't just close regedit or it will not save.  
Now you can reboot and login using the built in Administrator account.
Create a new account from command prompt.
```cmd
net user <username> /add
```

Now make the new account an administrator.
```cmd
net localgroup Administrators <username> /add
```

Now login with new account.
Once profile is created log out and log back in as the local administrator.
Now copy all the files from the old user directory to the new one of course minus the user registry and any system hidden files.  

In the new profile backup appdata folder and user,dat file.

Now open cmd as administrator.
```cmd
robocopy c:\users\<oldprofile>\Appdata c:\users\<newprofile>\Appdata /MIR /XJ /R:1 /W:1
```

Now open regedit again.
Click on users hive in the left pane.
Click on open hive and browse to the ntuser.dat file from the corrupt profile.
It is important to give it the same name as the next hive you open so if you use temp the next one also has to be called temp.  
Now go to temp and software. Right click and choose export and save it with a name like backup.
Click unload hive from the file menu.
Now click on open hive and browse to the ntuser.dat of the new profile.
don't forget to give it the same name as above. 
Then import the setting and all of your configuration should be there.  




