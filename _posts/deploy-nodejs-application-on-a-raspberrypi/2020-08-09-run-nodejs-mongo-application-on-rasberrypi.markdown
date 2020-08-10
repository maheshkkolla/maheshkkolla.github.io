---
layout: post
title:  "Run Nodejs and Mongo application on RaspberryPi running Ubuntu 20.04 using Docker and Docker Compose"
date:   2020-08-09
author: Mahesh Kumar Kolla
categories: deploy-nodejs-application-on-a-raspberrypi
tags:	tech raspberrypi ubuntu docker
placement: 4
prevPost: install-docker-and-docker-compose-on-ubuntu-raspberrypi  
---

Sub post of [Deploy Nodejs 12 and Mongodb 4.4 application on a RaspberryPi](deploy-nodejs-and-mongodb-application-on-a-raspberrypi)

{% include prev-next-nav.html %}

We are going to Dockerise the application and run it in the RaspberryPi using docker compose in this post.


- ##### Dockerising the application

  Create a `Dockerfile` from base image `arm64v8/node`
  
  Example:
  ```dockerfile
  
  FROM arm64v8/node:latest
  
  RUN mkdir -p /usr/src/app
  WORKDIR /usr/src/app
  COPY . /usr/src/app
  
  RUN npm install
  
  EXPOSE 8080
  CMD [ "npm", "start" ]
  ``` 

- ##### Docker compose with mongodb

  Create `docker-compose.yml` file combining the node application and mongodb
  
  Example:
  ```yaml
 
    version: "2"
    services:
      app:
        container_name: <your-container-name>
        restart: always
        build: .
        ports:
          - "8080:8080" 
        links:
          - mongo
        environment:
          - DB_URL=mongodb://mongo:27017
      mongo:
        container_name: mongo
        image: mongo
        volumes:
          - ./data:/data/db
        ports:
          - "27017:27017"
  ``` 
  
  In the above file, 
  - We are building the application image from the Dockerfile we created in the first step.
  - Pass any environment variables you want. Example: `DB_URL`
  - Mounting the volume for mongo container. Host `./data` (Change it according to your use case) is mounted to docker's `/data/db`
  - Exposing ports `8080` (Change according to your application) for application and `27017` for mongo database.   

- ##### Running the application on RaspberryPi
  
  - SSH into pi
  - Clone your repository in a directory you want 
  - Go to the repository using `cd`
  - Run `docker-compose up -d`
    
    This will build your application docker image and run the app and mongo db containers in detach mode.
    

- ##### Why to build the image in Pi and why not on Docker Hub?
  
  We are using arm64 nodejs image and it cannot be built in docker hub. 
  We will have to use cross-build container to do it. I have choose to build the image in Pi.
  Hence, did not explore that path.         

- #### That's it
  
  Now, You have your NodeJS and MongoDB application running on a RaspberryPi

{% include prev-next-nav.html %}
