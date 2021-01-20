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
- docker container ls: list all running containers;
- docker container stop containerId: stops the execution of the docker;
- docker container ls -a: list all container, running or not;
- docker run (do not use this one): runs a process in a isolated container;
- docker container run (use this one): runs a container;
- docker container run -d (or --detach): keeps the container on the foreground, even with no terminal opened;
- docker container run --publish 8080:80 --detach --name webserver nginx: name your container;
- docker container rm containerId containerId name: remove container;
- docker start containerId: start container;
- docker container top name containerId: list all process running inside the container;
- docker container inspect containerId: brings JSON of the configuration of our docker;
- docker container stats: estatísticas do docker;
- docker container run -it ubuntu /bin/bash: i = interactive / t = terminal / terminal = /bin/bash
- docker image rm imageName: removes image;
- docker exec: run command inside a container that is running (without getting inside it);
- docker exec -it containerId /bin/bash : enter the container and runs terminal of it;
- docker container rename containerId newContainerName: renames the container;
- docker container prune [OPTIONS]: it removes all the stopped containers (be careful);
- docker rmi [OPTIONS] IMAGE [IMAGE...] :  removes one or more images;
- docker images : see all images created and its id's;
- docker image inspect [IMAGEID] : check image JSON config (json metadata);
- docker container ls : see all containers and its id's;
- docker container inspect [CONTAINERID] : check image CONTAINER config (json metadata);
- docker volume ls:  Shows all volumes that docker creates;
- docker volume rm [VOLUMEID] removes the volume selected;

## DOCKER RUN ACTION
- Two signais: command to run (--);
- Shortcut to run (-);
- Port (port that the docker will use on the physical machine : port on the docker container);
- Name of the docker image

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
docker-compose up -d: Run the file with containers in dettach mode;
docker-compose stop: Stops the containers;
```

## DOCKER FILE
- [Official Reference](https://docs.docker.com/engine/reference/builder/);
- When you want to create your own image;
- When you want to update your image to Docker Hub;

## DOCKER EXAMPLES:

### FULL PROJECT IN 22 MINUTES
- [Check here](https://github.com/jvlessa/Docker-for-JavaScript---Node.JS/tree/main/22minutes--docker)

### NGINX IMAGE
- Docker Container Run NGINX direto do Docker Hub;
- Pull do Docker Hub, trazendo camadas, etc... tudo: ``docker pull nginx``;
- If you want a stable version version: ``docker pull nginx:stable``;
- If you want a stable latest version: ``docker pull nginx:latest``;
- List the Docker Images to see it downloaded: ``docker images``
- Servidor web (tipo Apache);
``docker container run -p 8080:80 nginx``
- Enter on the URL: http://localhost:8080/;
- NGINX will be running;
- If I want to keep this container running without terminal open, I can add the word "--detach" or "-d";
``docker container run -p 8080:80 --detach nginx``
``docker container run -p 8080:80 -d nginx``
- It will give you back the containerId;

### UBUNTU IMAGE
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

### AWS CLOUD 9 (SUPER CONTAINER)
- Is an enviroment of integrated development (IDE) online by Amazon;
``
docker pull sapk/cloud9
docker run -d -p 8181:8181 sapk/cloud9 --auth username:password
``

- Open: https://localhost:8181
- Type "username" and "password" to get in;
- Open the clouud9 IDE: https://localhost:8181/ide.html;

## VOLUMES
- [Official Doc](https://docs.docker.com/storage/volumes/);
- How do I share files, folders, etc between containers?
- Volumes are the prefered way to save generated data of containers;
- If you give an "docker container inspect [containerID]":
- You can see "Volumes" that will be stored, on the actual machine;
- You can see "Mounts" that will be store, on the actual machine;
- The "Source" parameter indicates where the container is currently storing data;
- On the Linux enviroment you will find where the files are;
- On the MAC or Linux, Docker makes an pseudo folder that only Docker knows;
- If we run: "docker volume ls" = Shows all volumes that docker creates;

- <b>So, how do we store data using volumes?</b>
- Simple! Use "$(pwd)" = (pwd is the current folder):
``docker run -d -v $(pwd):/workspace -p 8181:8181 sapk/cloud9 --auth username:password``
- If I run the command of the volume to the same directory (cloud 9 workspace, they will share files and folders);
- Do not think that different images will be sharing same thing, be careful;

## DOCKER CONTAINER COMMIT
- [Official Documentation](https://docs.docker.com/engine/reference/commandline/commit/);
- Creates a new image from a container's changes;
``docker container commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]``
- Example: Generating a new image - (locally):
``docker container commit -m "Added NVM and CURL" 6a1228458a3a``
- Get the hascode that cameback for you after running command: "sha256:b4554e2ba0343081d9c6f5ca7ae8b238e474129d272b9e527177b0828952d766";
- Run ``docker images`` and you'll see a image without a name or TAG;
- Stop the container that generated the image;
- Delete the container that generated the image;
- Now run the command below with the new [IMAGEID] created:
``docker run -d -v $(pwd):/workspace -p 8181:8181 [IMAGEID] --auth username:password``