---
layout: post
title:  "Installing docker - v2.8"
date:   2016-10-17 17:04:38 +0530
categories: docker, all
tags: docker
---
### How to install Docker ?

* #### On vanilla ubuntu instance 
There are many ways to install docker on your linux machine. Easiest way probably is to run this command on your terminal

                    curl -sSL https://get.docker.com/ | sh

This will download and run the script present on [get.docker.com](https://get.docker.com/) which will install docker on your machine.

* #### Installing manually on ubuntu
If you are cautious about third party scripts, you can install docker manually on your ubuntu instance by following the this process that is outlined [in docker documentation](https://docs.docker.com/engine/installation/linux/ubuntulinux/). Below is a handy script that does exactly the same that is outlined on that page.
            <script src="https://gist.github.com/penkeysuresh/f248ae77e26b6474de27f0a9c9093718.js"></script>

* #### On Amazon Linux AMI instance
Amazon has built in package manager ``yum`` which makes it easier to install docker on Amazon Linux AMI instance. Below is the simple command that's install docker 

                    sudo yum install -y docker

### Create a docker group

Docker always runs as root and can be accessed via sudo. For all the cases it is advised to create a group docker and add it to sudo and add your user to docker group instead of using sudo every time.

Create docker group using 

                    sudo groupadd docker

Add your user to docker group using 

                    sudo usermod -aG docker $(whoami)