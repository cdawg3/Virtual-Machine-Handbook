# IP Logger

### Create file
```bash
sudo nano /home/user/ip_logger.sh
```

### Add this to the file
```bash
#!/bin/bash
while true; do
  sudo tcpdump -i ens18 -n udp port 2456 | awk '{ if ($3 !~ /^192.168.1./ && $5 !~ /^192.168.1./) print $3 " -> " $5 }' | cut -d '.' -f 1-4 | tee /home/caleb/ip_addresses.log
  sleep 1 # to prevent high CPU usage if tcpdump exits quickly
done
```

### Make the script executable
```
chmod +x /home/caleb/ip_logger.sh
```

### Create file
```
sudo nano /etc/systemd/system/ip-logger.service
```

### Add this to the file
```
[Unit]
Description=IP Logger for UDP Port 2456

[Service]
ExecStart=/home/caleb/ip_logger.sh
Restart=on-failure
User=caleb

[Install]
WantedBy=multi-user.target
```

### Reload
```
sudo systemctl daemon-reload
```

### Enable service
```
sudo systemctl enable ip-logger.service
```

### Start service
```
sudo systemctl start ip-logger.service
```

### Check status
```
sudo systemctl status ip-logger.service
```

### Check logs
```
sudo journalctl -xe -u ip-logger.service
```
