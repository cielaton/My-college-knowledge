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