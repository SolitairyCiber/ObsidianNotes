This one may or may not change anything.  What it does is disables the "my info" screen in settings.  Some people say it cuts down on the nag screens for a MS account and some say it didn't do anything for them.  Either way it is not something many people find use for and never notice it missing.  From a elevated command prompt past the following.

```cmd
reg add "HKLM\SOFTWARE\Microsoft\PolicyManager\default\Settings\AllowYourAccount" /v value /t REG_DWORD /d 0
```

If for some reason you need it back.

```cmd
reg add "HKLM\SOFTWARE\Microsoft\PolicyManager\default\Settings\AllowYourAccount" /v value /t REG_DWORD /d 1
```

 Next lets shut off and disable the telemetry service.  This does seem to work at disabling some of the nag screens.  As a bonus it also stops MS from some of it's spying activity.  

```cmd
net stop DiagTrack
sc config "DiagTrack" start= disabled
```