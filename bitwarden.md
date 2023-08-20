### Create a bitwarden user
```
sudo adduser bitwarden
```
### Set password for bitwarden
```
sudo passwd bitwarden
```
### Create a docker group
```
sudo groupadd docker
```
### Add bitwarden to docker gorup
```
sudo usermod -aG docker bitwarden
```
### Create a bitwarden directory
```
sudo mkdir /opt/bitwarden
```
### Change permissions of the directory recursively
```
sudo chmod -R 700 /opt/bitwarden
```
### Change ownership of the directory recursively
```
sudo chown -R bitwarden:bitwarden /opt/bitwarden
```
#### Install Bitwarden installation script
```
curl -Lso bitwarden.sh "https://func.bitwarden.com/api/dl/?app=self-host&platform=linux" && chmod 700 bitwarden.sh
```
### Run the bitwarden installation script
```
./bitwarden.sh install
```

```
sudo nano ./bwdata/env/global.override.env
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

```

```

```

```

```

```

```

```
