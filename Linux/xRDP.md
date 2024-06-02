sudo apt update
sudo apt install xfce4 xfce4-goodies -y
sudo apt install xrdp -y
sudo systemctl status xrdp

If not started
sudo systemctl start xrdp

Stop xrdp with `sudo service xrdp stop`

Edit the xrdp start script: `sudo nano /etc/xrdp/startwm.sh`

In this file, replace the lines

```
test -x /etc/X11/Xsession && exec /etc/X11/Xsession
exec /bin/sh /etc/X11/Xsession
```

with `startxfce4`

(You can comment out lines by adding `#` at the start)

Restart xrdp with `sudo service xrdp start`

