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
```bash
chmod +x /home/user/ip_logger.sh
```

### Create file
```bash
sudo nano /etc/systemd/system/ip-logger.service
```

### Add this to the file
```bash
[Unit]
Description=IP Logger for UDP Port 2456

[Service]
ExecStart=/home/user/ip_logger.sh
Restart=on-failure
User=caleb

[Install]
WantedBy=multi-user.target
```

### Reload
```bash
sudo systemctl daemon-reload
```

### Enable service
```bash
sudo systemctl enable ip-logger.service
```

### Start service
```bash
sudo systemctl start ip-logger.service
```

### Check status
```bash
sudo systemctl status ip-logger.service
```

### Check logs
```bash
sudo journalctl -xe -u ip-logger.service
```
