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

https://templatemo.com/live/templatemo_615_amber_folio

The website layout and idea was adapted from the TemplateMo Amber Folio template, while the image gallery, CSS styling, filtering buttons, and lightbox functionality were customised for this project.

Main files located in - /var/www/html/index.html

5. Image upload

Create a folder, add photos to transfer

scp -i C:\Users\ahmaa\Downloads\yochi.pem -r %USERPROFILE%\Downloads\photos1\* azureuser@20.5.25.243:/tmp/

Images then moved into my Linux folder

sudo mkdir -p /var/www/html/photos 1

sudo chmod 644 /var/www/html/photos 1/

6. DNS setup
 
The domain was purchased through Name.com. A record was created pointing it towards the public IP of the VM

www.Jett.store to 20.5.25.243

7. SSL/TLS setup
HTTPS was set up using Certbot and Let's Encrypt

Selected Software: Nginx - System: Linux (snap)

Used the following commands in my Ubuntu VM

sudo snap install core

sudo snap refresh core

sudo snap install --classic certbot

sudo ln -s /snap/bin/certbot /usr/bin/certbot

sudo certbot --nginx

I then updated the NGINX configuration to enable HTTPS, and redirected the HTTP traffic to my domain
Jett.store

8. Script test
Script name - server-status.sh

This script generates a server status webpage for the ICT171 cloud server project. It collects basic server information, including the current date, server uptime, NGINX status, SSL/TLS status, disk usage, and memory usage

The script is stored on the server in: /home/azureuser/scripts/server-status.sh

The output file is created in: /var/www/html/status.html

The script output can be checked online at: https://jett.store/status.html

