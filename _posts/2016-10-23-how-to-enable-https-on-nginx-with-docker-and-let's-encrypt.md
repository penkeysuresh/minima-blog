---
layout: post
title:  "Enabling https using let's encrypt with docker - v2.6"
date:   2016-10-17 17:04:38 +0530
categories: docker, all
tags: docker, nginx, https
---
Let's encrypt is a certificate authority which issues free TSL/SSL certificates using which you can enable https for your domain. Using let's encrypts ``certbot`` utility you can create free SSL/TSL certificates for your website. 

In this tutorial we'll use let's encrypt to generate and install certificates on nginx inside docker container there by enabling https. Before continuing please make you have a registered domain and the ``A Record`` of the domain points to a server where you want to set-up your application 

### Step : 1

Based on what version your server is running your certbot installation will be different. You can check how to install certbot for a combination of server-OS on [certbot's website](https://certbot.eff.org/). 

For simplicity we'll use nginx with ubuntu 16.04 as server and OS. Run this command to install certbot client

        sudo apt-get install -y letsencrypt


### Step : 2

Install nginx on your server and configure it for certbot client. This will install and start nginx default site on port 80. You should be able to see nginx default page when you visit your domain after this.
        
        sudo apt-get install -y nginx

Now edit the default nginx configuration for certbot to include ~ /.well-known location block. 

Open the default nginx configuration ``sudo vi /etc/nginx/sites-available/default`` and add below block

    server {
        ...

        location ~ /.well-known {
                allow all;
        }

        ...
    }

### Step : 3

Generate certificates using below command. Be sure to replace example.com, www.example.com with your registered domain name. Enter your email and domain names if prompted.

        sudo letsencrypt certonly --webroot -w /usr/share/nginx/html -d example.com -d www.example.com 


### Step : 3.1 (optional)

Create a strong Diffie-Hellman Group

        sudo openssl dhparam -out /etc/ssl/certs/dhparam.pem 2048

### Step : 4
Stop the nginx. And build your docker container. Since we are using nginx to make the site https you'll have to add nginx to your 

















