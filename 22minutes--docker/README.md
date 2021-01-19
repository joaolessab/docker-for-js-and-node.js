# DOCKER IN 22 MINUTES

## RUNNING

### INSTALL DEPENDENCIES
On the folder `./api`, run:
```
npm install
```

Node dependencies will be installed.

### BUILDING IMAGES

Access the root folder of the project and build each image (MySQL, Node API e PHP):

```
docker build -t mysql-image -f api/db/Dockerfile .
```
```
docker build -t node-image -f api/Dockerfile .
```
```
docker build -t php-image -f website/Dockerfile .
```

### RUNNING CONTAINERS
On the root folder, execute each one:

```
docker run -d -v $(pwd)/api/db/data:/var/lib/mysql --rm --name mysql-container mysql-image
```
```

docker run -d -v $(pwd)/api:/home/node/app -p 9001:9001 --link mysql-container --rm --name node-container node-image
```
```
docker run -d -v "$(pwd)/website":/var/www/html -p 8888:80 --link node-container --rm --name php-container php-image
```

### NOW DO THE DATABASE RESTORE
```
docker exec -i mysql-container mysql -uroot -pprogramadorabordo < api/db/script.sql
```

### ACCESSING URL'S:
https://localhost:9001/products
https://localhost:8888