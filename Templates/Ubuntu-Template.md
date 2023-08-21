# Ubuntu Template Tutorial
Source video [Launching a Virtual Machine](https://www.youtube.com/watch?v=xBUnV2rQ7do&list=PLT98CRl2KxKHnlbYhtABg6cF50bYa8Ulo&index=6).  
Source video [Creating Virtual Machine Templates](https://www.youtube.com/watch?v=t3Yv4OOYcLs&list=PLT98CRl2KxKHnlbYhtABg6cF50bYa8Ulo&index=7).  


## Initial setup

### Update and upgrade
```
sudo apt update && sudo apt dist-upgrade
```

### Install the guest agent
```
sudo apt install qemu-guest-agent
```

### Check the status of the guest agent
```
sudo systemctl status qemu-guest-agent.service
```

### Attempt to start the guest agent
```
sudo systemctl start qemu-guest-agent.service
```

### Enable the quest agent


### Power off the VM
```
sudo poweroff
```

### Start the VM


## Change the SSH host keys

### View the key locations
```
ls -l /etc/ssh
```

### Check that cloud-init is installed
```
apt search cloud-init
```

### If not installed
```
sudo apt install cloud-init
```

### Change directory
```
cd /etc/ssh
```

### Remove the host keys
```
sudo rm ssh_host_*
```
