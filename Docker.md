### Update package information
```
sudo apt-get update
```
### Install prerequisites
```
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```
### This
 
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
### Or this
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o docker.gpg
```

```
sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg docker.gpg
```

```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
### Update package information again
```
sudo apt-get update
```
### Install docker
```
sudo apt-get install docker-ce
```
### Install docker compose
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
### Make the binary executable
```
sudo chmod +x /usr/local/bin/docker-compose
```
### Add user to docker group
```
sudo usermod -aG docker $USER
```
