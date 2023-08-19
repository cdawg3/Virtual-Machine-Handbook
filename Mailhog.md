### Install Mailhog
```
wget https://github.com/mailhog/MailHog/releases/download/v1.0.1/MailHog_linux_amd64
```
### Make Mailhog executable
```
chmod +x MailHog_linux_amd64
```
### Move Mailhog to the /usr/bin/local directory
```
sudo mv MailHog_linux_amd64 /usr/local/bin/mailhog
```
### allow tcp on port 8025
```
sudo ufw allow 8025/tcp
```
### Run mailhog for the first time
```
mailhog
```
### Create file for mailhog service

```
sudo nano /etc/systemd/system/mailhog.service
```
### Put this in the file
```
[Unit]

Description=Mailhog

[Service]
User=username
ExecStart=/usr/local/bin/mailhog

[Install]
WantedBy=multi-user.target
```
### Run these to enable and start Mailhog service
```
sudo systemctl daemon-reload
```

```
sudo systemctl enable mailhog
```

```
sudo systemctl start mailhog
```
### Check that mailhog is running
```
sudo netstat -tuln | grep 8025
```
![image](https://github.com/cdawg3/Virtual-Machine-Handbook/assets/99144314/c932d8f2-9d33-4a6d-ab09-31b1f1de0abb)

### Visit Mailhog
```
http://your-servers-ip:8025
```
