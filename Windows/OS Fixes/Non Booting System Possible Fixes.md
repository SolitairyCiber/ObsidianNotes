Backup users directory.
``` c
robocopy /E /V /B /R:0 /XD:"c:\users\all users\application data" c:\users d:\users d:\backupdrive
```


``` C 
DISM /Online /Cleanup-Image /CheckHealth
DISM /Online /Cleanup-Image /StartComponentCleanup 
DISM /Online /Cleanup-Image /AnalyzeComponentStore
```


From recovery boot.  

``` C 
dism /image:c:\ /cleanup-image /restorehealth /source:c:\windows
```


If you get source files can not be found.
Boot to a USB with the same version of windows and go into recovery mode again.

``` c

dism /image:c:\ /cleanup-image /restorehealth /source:d:\sources\install.esd
```

Next.
``` c
sfc /scannow /offbootdir=c: /offwindir=c:\windows 
```


Fix MBR boot loader.

``` c 
/source:WIM:L:\sources\install.wim:1
```
