# IP Logger

### Create file
```bash
sudo nano /home/user/full_logger.sh
```

### Add this to the file
```bash
#!/bin/bash
while true; do
  sudo tcpdump -i ens18 -n udp port 2456 | awk '{ if ($3 !~ /^192.168.1./ && $5 !~ /^192.168.1./) print strftime("%Y-%m-%d %H:%M:%S") " " $3 " -> " $5 " Length: " $NF }' | cut -d '.' -f 1-7 | tee /home/caleb/full_details.log
  sleep 1 # to prevent high CPU usage if tcpdump exits quickly
done
```

### Make the script executable
```bash
chmod +x /home/user/full_logger.sh
```

### Create file
```bash
sudo nano /etc/systemd/system/full-logger.service
```

### Add this to the file
```bash
[Unit]
Description=Full Logger for UDP Port 2456

[Service]
ExecStart=/home/user/full_logger.sh
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
sudo systemctl enable full-logger.service
```

### Start service
```bash
sudo systemctl start full-logger.service
```

### Check status
```bash
sudo systemctl status full-logger.service
```

### Check logs
```bash
sudo journalctl -xe -u full-logger.service
```
