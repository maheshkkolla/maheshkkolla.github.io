---
layout: post
title:  "Deploy Nodejs 12 and Mongodb 4.4 application in RaspberryPi"
date:   2020-08-09
author: Mahesh Kumar Kolla
categories: deploy-nodejs-application-on-a-raspberrypi
tags:	tech nodejs raspberrypi mongodb 
---


I was excited to buy a RaspberryPi 4 to setup a small own personal server. 
I always wanted to write tools/utils by my own and deploy it on my personal server.
But It turned out to be a stress full thing to deploy my NodeJS 12 and Mongodb 4.4 (anything about 3) on the RaspberryPi 4.
Hence, I have decided to write it down. 

RaspberryPi comes with Raspbian OS installed with it. It is 32 bit OS (Raspbian 64 bit beta is released) and the hardware is arm64 bit architecture.
These are main reasons for me it took long to setup and deploy.
Mongodb does not support 32 bit arm64 architecture in it's latest versions. You can install very old versions in RaspberryPi (Raspbian 32 bit).
You cannot even use mongo docker image latest versions (https://hub.docker.com/_/mongo) in 32 bit OS. 
Hence, the first thing to do it change the OS in RaspberryPi. I have decided to use Ubuntu Server. (Optionally you can install the desktop in it)


#### STEP-1: [Install Ubuntu Server on a RaspberryPi 4](install-ububtu-server-on-a-raspberrypi)       
