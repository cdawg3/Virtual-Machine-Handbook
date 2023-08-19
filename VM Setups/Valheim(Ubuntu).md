Here is the [source video](https://youtu.be/gVUlcsiPFxA)

[Additional resource 1](https://developer.valvesoftware.com/wiki/SteamCMD)

[Additional resource 2](https://steamcommunity.com/sharedfiles/filedetails/?id=2383801614)

### Update and upgrade system
```
sudo apt update
```

```
sudo apt upgrade
```
### Add necessary repository and architecture
```
sudo add-apt-repository multiverse
```

```
sudo dpkg --add-architecture i386
```

```
sudo apt update
```
### Install steamcmd
```
sudo apt install steamcmd
```

```
steamcmd +login anonymous +force_install_dir /home/user/steamcmd +app_update 896660 validate + exit
```

```
cd ./steamcmd/
```
### Change name, world, and password
```
nano start_server.sh
```
![image](https://github.com/cdawg3/Virtual-Machine-Handbook/assets/99144314/175a226e-c025-41b7-b7c8-5be3828d80fd)

### See if server starts
```
sh start_server.sh
```
### Port forwarding
```
sudo apt install net-tools
```

```
ifconfig
```

```
sudo ufw allow 2456:2458/tcp
```

```
sudo ufw allow 2456:2458/udp
```
### Setup Valheim service
```
sudo nano /etc/systemd/system/valheim.service
```

```
[Unit]
Description=Valheim Server

[Service]
User=username
WorkingDirectory=/home/user/steamcmd
ExecStart=/home/user/steamcmd/start_valheim.sh
Restart=always

[Install]
WantedBy=multi-user.target
```

```
sudo systemctl daemon-reload
```

```
sudo systemctl enable valheim
```

```
sudo systemctl start valheim
```

```
sudo systemctl status valheim
```
![image](https://github.com/cdawg3/Virtual-Machine-Handbook/assets/99144314/fb67e079-7265-4e19-aa8f-0b72c447d2a9)

### Check logs to see if it's working
```
sudo journalctl -u valheim -f
```
