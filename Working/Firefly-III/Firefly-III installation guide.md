> This documentation assumes that you have already installed an operating system to host the project, such as the Ubuntu server.
---
### Dependencies
First, update the apt package manager database with:
```bash
sudo apt update
```
##### Apache
Install Apache web server:
```bash
sudo apt install apache2
```
The installation will prompt you to ask if you want to continue, choose yes for all similar package installations using apt from now on.

For testing purposes, configure Firewall to enable only port 80 (normal, unencrypted traffic):
```bash
sudo ufw allow in "Apache"
```

You can try to access the running server using an external device, make sure to connect to the same network with the server.
First, find the public IP of the server using
```bash
ip addr
```
Expected output:
![[Screenshot_20240306_110055.png]]
Here, in the enp0s3 section, my IP address is 10.10.40.138
So I will type into the URL bar in the browser from another device:
`http://10.10.40.138`

Expected output:![[Screenshot_20240306_110203.png]]

##### MySQL
Install MySQL:
```bash
sudo apt intall mysql-server
```
Start the interactive script using:
```bash
sudo mysql_secure_installation
```
This will ask if you want to configure the `VALIDATE PASSWORD PLUGIN`
-> Choose yes
About the password validation level, choose MEDIUM or STRONG as you prefer.
Remove anonymous user? -> Yes
Disallow root login remotely? -> Yes
Remove test database and access to it? -> No

Finally, check to see if MySQL is up and running:
```bash
sudo mysql
```
Expected output:
![[Screenshot_20240306_111153.png]]

Then type `exit` to quit the interactive environment.
##### PHP
Save existing PHP package list to packages.txt file:
```bash
sudo dpkg -l | grep php | tee packages.txt
```
Add the repo for PHP 
```bash
sudo add-apt-repository ppa:ondrej/php # Press enter when prompted.
sudo apt update
```