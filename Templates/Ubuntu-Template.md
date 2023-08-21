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
![image](https://github.com/cdawg3/Virtual-Machine-Handbook/assets/99144314/6784eb24-d79d-40b2-963f-111bf358e50a)

### Check that cloud-init is installed
```
apt search cloud-init
```
![image](https://github.com/cdawg3/Virtual-Machine-Handbook/assets/99144314/7cfe2282-3ba4-44ea-8097-c3d151420043)

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
![image](https://github.com/cdawg3/Virtual-Machine-Handbook/assets/99144314/c4201926-e80f-4aac-ad39-a83ab96a9855)

## Empty machine ID

### View machine ID
```
cat /etc/machine-id
```

### Empty out the machine-id file
```
sudo truncate -s 0 /etc/machine-id
```

### Check for symbolic links
```
ls -l /var/lib/dbus/machine-id
```
![image](https://github.com/cdawg3/Virtual-Machine-Handbook/assets/99144314/f3fa0e0b-b8da-4737-8f74-88cbc178951f)

### If no symbolic link then create one
```
sudo ln -s /etc/machine-id /var/lib/dbus/machine-id
```














































