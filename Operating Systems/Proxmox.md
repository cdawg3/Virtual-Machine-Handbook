# Proxmox Setup

### Check that internet is working
```
ip a
```

look for this line or one similar (it is probably towards the bottom):
*vmbr0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state UP group default qlen 1000
 inet 192.168.1.130/24 brd 192.168.1.255 scope global eth0*

 ** If using a server with iLO make sure ethernet is plugged in iLO and standard ethernet **

### If DOWN and not UP try this:
```
ip link set INTERFACE_NAME up
```
### Edit enterprise and subscription files
```
nano /etc/apt/sources.list
```
### Add these lines
```
# Not for production use
deb http://download.proxmox.com/debian name pve-no-subscription
```
### Check the sources.list.d directory
```
ls /etc/apt/sources.list.d
```
### Comment out the only line in each file. Example files: 
```
nano /etc/apt/sources.list.d/pve-enterprise.list
nano /etc/apt/sources.list.d/ceph.list
```
### Update and upgrade
```
apt-get update
```

```
apt-get upgrade
```

```
reboot
```
### Add user and elevate privileges
```
adduser username
```

```
apt-get install sudo
```

```
usermod -aG sudo username
```

```
su - username
```
### Test to see if it worked
```
sudo ls /root
```
### Or
```
sudo ls -a root
```

```
reboot
```

```

```

```

```

```

```

```

```

```

```

```

```

```

```
