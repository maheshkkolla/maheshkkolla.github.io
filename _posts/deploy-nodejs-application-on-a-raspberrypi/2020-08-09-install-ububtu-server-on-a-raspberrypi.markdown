---
layout: post
title:  "Install Ububtu 20.04 Server on a Raspberry Pi 4"
date:   2020-08-09
author: Mahesh Kumar Kolla
categories: deploy-nodejs-application-on-a-raspberrypi
tags:	tech raspberrypi ubuntu  
---

Sub post of [Deploy Nodejs 12 and Mongodb 4.4 application in RaspberryPi](deploy-nodejs-and-mongodb-application-in-raspberrypi)

Let's go through the process of installing Ubuntu 20.04, Connect to WiFi, SSH into it and Install desktop (optionally) in this post.


- ##### We need to have an imager to create the bootable SD Card. 
  
  Download and install the respective imager from [here](http://downloads.raspberrypi.org/imager/) (MacOS, Windows, Linux)

- ##### Making bootable SD Card
    
    - Insert the SD Card to the computer/laptop
    - Open the imager, You see 3 steps like Choose OS, Choose SD Card, Write 
    - Select "Choose OS" -> "Ubuntu" -> "Ubuntu 20.04 LTS (Pi 3/4)"
      
      Note: Make sure you are selecting the 64 bit OS for arm64 architectures
    - Choose the SD card to write
    - Click on "Write". It will take some time to write into the SD Card 
   
- ##### Connecting to Wifi
    
    - Remove and insert the SD again to the computer/laptop
    - Open the `system-boot` drive 
    - Edit the `network-config` file with your WiFi configuration
    - Uncomment the `wifis` block in the file and add your WiFi credentials
        ```yaml
            wifis:
              wlan0:
              dhcp4: true
              optional: true
              access-points:
                "<WiFi name>":
                  password: "<WiFi password>"
        ```
      Note: Include quotes if there are spaces in the name or password.       
    - Save the file and Eject the SD Card from the computer/laptop.
    
- ##### Booting the Pi and SSH
    
    - Just insert the SD card into the Pi and connect it to the power.
    - It takes around a minute to boot the Pi with the Ubuntu you just installed
    - Find out the IP Address of the Pi
    - `ssh ubuntu@<Pi's IP address>` Example: `ssh ubuntu@<192.168.0.5>`
    - Confirm the connection by typing `yes`
    - `ubuntu` is the default password for user `ubuntu`
    - It will ask to change the password on the first time login
    - Login again with the changed password
    
- #### Optional: Install desktop
    
    If you want the desktop then, You can install any light weight desktop of your wish.
    I have installed `kubuntu-desktop` which is fine but not great.
    
    - `sudo apt update` and `sudo apt upgrade`
    - `sudo apt install kubuntu-desktop`
    - `sudo reboot` to reboot the pi and start the desktop
    - Ideally, You new desktop should come up automatically. But in some cases it does not.
     Hence, you can run `startx` to start the desktop.
     
Boom..... That's all. You have a RaspberryPi running Ubuntu 64 bit OS in it.              
