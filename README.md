<h1 align="center"><b>DOCKER FOR JAVASCRIPT & NODE.JS</b></h1>

<p align="center">
  <img src="https://raw.githubusercontent.com/jvlessa/Docker-for-JavaScript---Node.JS/main/media/docker_logo.png" width="350">
</p>

- Repository focused on: Creation of Enviroments for running JS / Node.JS apps;

## DOCKER DOCUMENTATION
- Please, find it [here](https://www.docker.com/get-started);
- Docker <b>is not a Virtual Machine</b>;
- Docker <b>is a software containerization platform</b>;

## CONTAINER VS. VIRTUAL MACHINES
- They have similar resource isolation and allocation benefits, but works differently because <b>containers virtualize the operating systems</b> and <b>virtual machines virtualize hardware</b>;
- Containers are more portable and efficient;

- Virtual Machines <b>use more HARDWARE</b> from your computer and subtract the resources;
- Containers use <b>only what the application that is running</b> needs (they basically just have the libs and the application);

<p align="center">
  <img src="https://raw.githubusercontent.com/jvlessa/Docker-for-JavaScript---Node.JS/main/media/containerVSvirtualmachine.png" width="800">
</p>

## INSTALLING DOCKER
- [Official page](https://docs.docker.com/get-docker/);
- [Windows](https://docs.docker.com/docker-for-windows/install/);
- [Linux](https://docs.docker.com/engine/install/);
- [MAC](https://docs.docker.com/docker-for-mac/install/);

## CHECKING IF EVERYTHING IS OKAY, AFTER INSTALLATION
- Check version: ``docker -v``
- Checking Hello World: ``docker run hello-world``
- Checking Docker Images: ``docker images``
- Containers pulled so far (history): ``docker ps -a``
- If you want to see only the containers that are running (running state): ``docker ps``

## DOCKER HUB
- Basically it's the Docker Official Repository with ready-to-use images;
- [Docker Hub: Official Website](https://hub.docker.com/);

## IMAGE
- It's the application that you want to use it;
- Example: Ubuntu, Office 2010;

## CONTAINER
- It's an instance of the IMAGE;
- It's a process of the IMAGE running;
- We can have lots of CONTAINERS running one IMAGE;
<p align="center">
  <img src="https://raw.githubusercontent.com/jvlessa/Docker-for-JavaScript---Node.JS/main/media/imagevscontainerdocker.png" width="800">
</p>

## DOCKER COMMANDS
- <b>Docker Sintaxe:</b> docker <command> <sub command> (options);
- [Check it here](https://docs.docker.com/engine/reference/commandline/docker/);
- docker: list all commands;
- docker version;
- docker container ls: List all running containers;
- docker container stop containerId: stops the execution of the docker;
- docker container ls -a: list all container, running or not;
- docker run (do not use this one): runs a process in a isolated container;
- docker container run (use this one): runs a container;
- docker container run -d (or --detach): keeps the container on the foreground, even with no terminal opened;
- docker container run --publish 8080:80 --detach --name webserver nginx: name your container;
- docker container rm containerId containerId name: remove container;
- docker container containerId start: start container;
- docker container top name containerId: list all process running inside the container;
- docker container inspect containerId: brings JSON of the configuration of our docker;
- docker container stats: estatísticas do docker;
- docker container run -it ubuntu /bin/bash: i = interactive / t = terminal / terminal = /bin/bash

## DOCKER RUN ACTION
- Two signais: command to run (--);
- Shortcut to run (-);
- Port (port that the docker will use on the physical machine : port on the docker container);
- Name of the docker image

## RUNNING A CONTAINER (PRACTICING)
- Docker Container Run NGINX direto do Docker Hub;
- Pull do Docker Hub, trazendo camadas, etc... tudo: ``docker pull nginx``;
- If you want a stable version version: ``docker pull nginx:stable``;
- If you want a stable latest version: ``docker pull nginx:latest``;
- List the Docker Images to see it downloaded: ``docker images``

## DOCKER: NGINX
- Servidor web (tipo Apache);
``docker container run -p 8080:80 nginx``
- Enter on the URL: http://localhost:8080/;
- NGINX will be running;
- If I want to keep this container running without terminal open, I can add the word "--detach" or "-d";
``docker container run -p 8080:80 --detach nginx``
``docker container run -p 8080:80 -d nginx``
- It will give you back the containerId;

## DOCKER: UBUNTU WITH TERMINAL
``
docker pull ubuntu
docker container run -it ubuntu /bin/bash
git -v
git --version
apt-get update
apt-get install git
git -v
git --version
exit
``

- Me juntar ao container novamente:
``
docker container ls
docker container attach containerId
enter to get into ubuntu terminal prompt
``

## DOCKER COMPOSE
- Way of organizing and manager all of your containers using 1 file with ".yml" extension;
- You can configure everything easier;
- [Official reference](https://docs.docker.com/compose/);

- <b>Docker File vs. Docker Compose</b>:
- Docker File: you specify the image and everything that the image must have (os system, libs, etc);
- Docker Compose: manager containers in a unique file, configuration, links between containers, etc;

- Main commands (enter the directory folder to run it):
```
docker-compose up: Run the file with container;
docker-compose up -d: RUn the file with containers in dettach mode;
docker-compose stop: Stops the containers;
```

## DOCKER FILE
- When you want to create your own image;
- When you want to update your image to Docker Hub;