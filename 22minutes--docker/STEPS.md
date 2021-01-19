## STEPS FOR THE 22 MINUTES PROJECT

1. Install Docker;
2. Create [Docker File](https://docs.docker.com/engine/reference/builder/) inside "api/db" using mysql image for container from Docker Hub;
3. Use the image reference on Docker Hub to create the parameters you want;
4. Enter the root project folder and run: ``docker build -t mysql-image -f api/db/Dockerfile .``
5. Waits for Docker to load and configure everything (do not forget the "." at the end of this last command);
6. Type ``docker image ls`` to check if everything went right;
7. Then, we are going to create our container with the image that we just created;
8. Run the command ``docker run -d --rm --name mysql-container mysql-image``;
9. Run ``docker ps`` to check if the container is up and running;
10. Create a file called "script.sql" on the db folder;
11. Execute this command to execute command inside the container we just created (mysql-container in this case): ``docker exec -i mysql-container mysql -uroot < api/db/script.sql``

https://www.youtube.com/watch?v=Kzcz-EVKBEQ