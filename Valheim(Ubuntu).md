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
