# ICT171 Setup Guide

1. Azure VM Setup
The server was created using Microsoft Azure for Students. The VM runs Ubuntu Linux and is accessed using SSH.

VM details:
- Provider: Microsoft Azure
- Operating system: Ubuntu Linux
- Web server: NGINX
- Public IP address: 20.5.25.243

2. Connecting to the VM
Command used:

In CMD bash
C:\Users\ahmaa\Downloads\ ssh -i yochi.pem azureuser@20.5.25.243

3. Installing Nginx

sudo apt update
sudo apt install nginx
sudo systemctl status nginx

4. Website file location
Files are stored in - /var/www/html/
Main files located in - /var/www/html/index.html

5. Image upload
scp -i C:\Users\ahmaa\Downloads\yochi.pem -r %USERPROFILE%\Downloads\photos1\* azureuser@20.5.25.243:/tmp/

Images then moved into my Linux folder
sudo mkdir -p /var/www/html/photos 1
sudo chmod 644 /var/www/html/photos 1/

6. DNS setup
The domain was purchased through Name.com. A record was created pointing it towards the public IP of the VM

Jett.store to 20.5.25.243

7. SSL/TLS setup
HTTPS was set up using Certbot and Let's Encrypt
Selected Software: Nginx System: Linux (snap)

Used the following commands in my Ubuntu VM
sudo snap install core
sudo snap refresh core
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --nginx

I then updated the NGINX configuration to enable HTTPS, and redirected the HTTP traffic to my domain
Jett.store








