set password.
```bash
x11vnc -storepasswd
```

Accept default location.

Now start the server.

```bash
/usr/bin/x11vnc -xkb -forever -auth /var/run/lightdm/root/:0 -display :0 -rfbauth /root/.vnc/passwd -rfbport 5900 -bg -o /var/log/x11vnc.log
```

