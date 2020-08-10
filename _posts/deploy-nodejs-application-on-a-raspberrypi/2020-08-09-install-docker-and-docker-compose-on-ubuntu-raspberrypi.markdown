---
layout: post
title:  "Install Docker and Docker Compose on a RaspberryPi running Ubuntu 20.04"
date:   2020-08-09
author: Mahesh Kumar Kolla
categories: deploy-nodejs-application-on-a-raspberrypi
tags:	tech raspberrypi ubuntu docker
placement: 3
prevPost: install-ububtu-server-on-a-raspberrypi 
nextPost: run-nodejs-mongo-application-on-rasberrypi
---

Sub post of [Deploy Nodejs 12 and Mongodb 4.4 application on a RaspberryPi](deploy-nodejs-and-mongodb-application-on-a-raspberrypi)

{% include prev-next-nav.html %}

In this post, We will install Docker and Docker Compose on a RaspberryPi running Ubuntu 20.04 


- ##### Install Docker
  
  `curl -sSL https://get.docker.com | sh`

- ##### Change permissions 

  This will help to run docker commands without using sudo

  `sudo usermod -aG docker pi`
  
  Note: You need to reboot to run docker without sudo
     
- ##### Install the dependencies for docker-compose

  `sudo apt-get install libffi-dev libssl-dev`
  
  `sudo apt-get install python3 python3-pip`
  
- ##### Install docker compose
  
  `sudo pip3 install docker-compose`
  
  Docker compose installation takes time. If you want to see the feedback then you can run the command with `-v` (verbose mode)   

- ##### Test docker and docker-compose

  `docker -v` or you can pull a sample image and run it 

  `docker-commpose -v`

{% include prev-next-nav.html %}
