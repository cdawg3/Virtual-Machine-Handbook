Here is the [source video](https://youtu.be/-bPa5i2OtdI)

### Update and upgrade the system
```
sudo apt-get update
```

```
sudo apt-get upgrade
```
### Install unzip and begin setup
```
sudo apt install unzip
```

```
wget https://terraria.org/api/download/pc-dedicated-server/terraria-server-1449.zip
```

```
unzip terraria-server-1449.zip
```

```
cd /1449/Linux
```

```
chmod 775 TerrariaServer.bin.x86_64
```

```
./TerrariaServer.bin.x86_64
```
### Configure ssh and port
```
sudo ufw allow ssh
```

```
sudo ufw allow 7777
```

```
sudo ufw enable
```
### Create config file and service
```
sudo find /home -type f -name "*.wld"
```

```
sudo nano /home/user/1449/Linux/serverconfig.txt
```

```
world=/path/to/world/file
```

```
sudo nano /etc/systemd/system/terraria.service
```

```
[Unit]
Description=Terraria Server
After=network.target

[Service]
User=yourusername
WorkingDirectory=/path/to/terraria-server
ExecStart=/path/to/terraria-server/TerrariaServer.bin.x86_64 -config /path/to/terraria-server/serverconfig.txt
Restart=always
RestartSec=3

[Install]
WantedBy=multi-user.target
```

```
sudo systemctl daemon-reload
```

```
sudo systemctl enable terraria.service
```

```
sudo systemctl start terraria.service
```

```
sudo systemctl status terraria.service
```
