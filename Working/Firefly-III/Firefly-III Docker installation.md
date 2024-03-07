
> This documentation assumes that you have already installed an operating system to host the project, such as the Ubuntu server.
> We will use Docker to install the project since it's the most optimal method.

>For most of the given commands, you can just copy-pate them to your terminal.
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

### Firefly-III
Create a directory to store installation files:
```bash
mkdir firefly_install && cd firefly_install
```
Download the docker compose file:
```bash
wget https://raw.githubusercontent.com/firefly-iii/docker/main/docker-compose-importer.yml
```
Download configuration files:
```bash
wget https://raw.githubusercontent.com/firefly-iii/firefly-iii/main/.env.example -O .env
```
```bash
wget https://raw.githubusercontent.com/firefly-iii/docker/main/database.env -O .db.env
```
```bash
wget https://raw.githubusercontent.com/firefly-iii/data-importer/main/.env.example -O .importer.env
```

Using your favorite text editor to edit the downloaded file:
>[!note] For example, I'm using Neovim
>First install neovim with:
>```bash
>sudo apt install neovim
>```
>Then edit the file, for example with .env file:
>```bash
>nvim .env
>```
>will bring you to an editing view:
>![[Pasted image 20240307082009.png]]
>Using the arrow keys, head to the desired line.
>Press the key "i" to enter insert mode, then edit the file.
>After that, press "esc" to quit insert mode, and press the exact key as follow: ": (shift + ;)" then "w" then "q" then "enter" to save and quit.

What you need to do is:
- Change the `DB_PASSWORD` in `.env` to something else. Pick a nice password.
	For example: `DB_PASSWORD=none`
- Change `MYSQL_PASSWORD` in `.db.env` to the SAME password value
	For example: `MYSQL_PASSWORD=none`
- Change `FIREFLY_III_URL` in `.importer.env` to `http://app:8080`
- Change `VANITY_URL` in `.importer.env` to `http://localhost`

Start the container:
```bash
sudo docker compose -f docker-compose.yml up -d --pull=always
```
Expected output:
![[Pasted image 20240307083812.png]]

>[!note]
>The server is now up and running.

To access the site through an external device, make sure to connect to the same network as the server, and obtain the server IP address:
```bash
ip addr | grep enp0s3
```
For example, my output is:
![[Pasted image 20240306163010.png]]
So the IP address will be: `192.168.0.13`
Open a browser from another device, then get to
`http://192.168.0.13`
Expected output:
![[Pasted image 20240306163210.png]]

You now have a fully functional application!

##### Firefly III Data Importer
First, register an account and login.
Browse to Options section in the left menu bar, the head to Profile→ OAuth.
Choose "Create new client", then enter the information as follows:
![[Pasted image 20240307085325.png]]
Make sure to input the correct Redirect URL and uncheck the Confidential option.
Expected result
![[Pasted image 20240307085831.png]]

Now browse to the data importer at the same IP address but different port:
`http:192.168.0.13:81`
where 81 is the port.

Expected result:
![[Pasted image 20240307091431.png]]

Enter the Client ID from the previous step. In my example, it is "9":