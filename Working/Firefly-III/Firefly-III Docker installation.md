
> This documentation assumes that you have already installed an operating system to host the project, such as the Ubuntu server.
---
### Dependencies
First, update the apt package manager database with:
```bash
sudo apt update
```

##### Docker
Uninstall old versions:
```bash
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
This step is just to make sure there are no docker dependencies installed on your system, `apt-get` might report that you have none of these packages installed.

Set up the repository:
```bash
sudo apt-get update
```
```bash
sudo apt-get install ca-certificates curl
```
```bash
sudo install -m 0755 -d /etc/apt/keyrings
```
```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```
```bash
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
Add the repository to apt sources:
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

Install Docker:
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
Verify that the Docker Engine installation is successful by running the `hello-world` image:
```bash
sudo docker run hello-world
```
Expected output:
![[Screenshot_20240306_155718.png]]

##### Firefly-III Docker
Create a directory to store installation files:
```bash
mkdir firefly_install && cd firefly_install
```
Download the docker compose file:
```bash
wget https://raw.githubusercontent.com/firefly-iii/docker/main/docker-compose.yml
```
Download configuration files:
```bash
wget https://raw.githubusercontent.com/firefly-iii/docker/main/docker-compose.yml -O .env
```
```bash
wget https://raw.githubusercontent.com/firefly-iii/docker/main/database.env -O .db.env
```

Using your favorite text editor:
- Change the `DB_PASSWORD` in `.env` to something else. Pick a nice password.
	For example: `DB_PASSWORD=none`
- Change `MYSQL_PASSWORD` in `.db.env` to the SAME password value
	For example: `MYSQL_PASSWORD=none`
