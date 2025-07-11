Install Linux in VM. I am using Mint for this.
Download openvpn autologin profile.  If it does not exist enable it in the admin portal for the user you want to use.  

```
openvpn profile-xxx.ovpn
```

## Install requirements:
### SSH:
```
apt install ssh
systemctl enable ssh
```

### RDP client:
```
apt install remmina
```

### Keepass:
```
apt install keepass2
```

### Powershell:
Prerequisites: 
```
apt install -y apt-transport-https ca-certificates curl software-properties-common
```
Download powershell:
```
wget https://github.com/PowerShell/PowerShell/releases/download/v7.5.2/powershell_7.5.2-1.deb_amd64.deb
```
Install:
```
dpkg -i powershell_7.5.2-1.deb_amd64.deb
```


