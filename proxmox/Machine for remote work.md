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
Download pgp key:
```
wget -q -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /usr/share/keyrings/powershell.gpg > /dev/null
```
Add repository:
```
add-apt-repository "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/powershell.gpg] https://packages.microsoft.com/repos/microsoft-ubuntu-$(lsb_release -cs)-prod $(lsb_release -cs) main"
```
Update:
```
apt update
```


