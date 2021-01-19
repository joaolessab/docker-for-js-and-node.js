1. Install Docker;
2. Create [Docker File](https://docs.docker.com/engine/reference/builder/) inside "api/db" using mysql image for container from Docker Hub;
3. Use the image reference on Docker Hub to create the parameters you want;
4. Enter the root project folder and run: ``docker build -t mysql-image -f api/db/Dockerfile .``
5. Waits for Docker to load and configure everything (do not forget the "." at the end of this last command);
6. Type ``docker image ls`` to check if everything went right;