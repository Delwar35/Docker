# Docker Compose

Docker compose file (.yml files e.g. docker-compose.yml) can be used to create multiple images. 

inside Docker Compose file:

```
services:
 ngin_server:
  container_name: nginx1 <give a container name>
  image: nginx:latest <can put name of existing image>
  port:
    - "80:80"
  
  ngin_server2:
  container_name: nginx2 <give a container name>
  image: nginx:latest <can put name of existing image>
  port:
    - "81:80" <formate localhost-port:port-required> in this case the nginx2 is being forwared to port 81 instead of port 80
   

  ngin_server3:
  container_name: nginx2 <give a container name>
  image: wrire-name-of-image-tobuild <if you want to build an image and not use an exisying one>
  build:
    context: . <location of dockerfile>
    dockerfile: nginx1.dockerfile <name of dockerfile>

    
  port:
    - "83:80"
```
creating containers in the same network so that they can communicate with each other

```
services:
 app:
  container_name: nodeapp
  network:
   - app-db-network
  links:
   - db
  depends_on:
   - db

 
 db:
  container_name: db
  network:
   - app-db-network

 network:
  app-db-network
   driver: bridge
```

 Run through terminal
 
`docker compose build` - will look at the docker compose file and build the image
can add `-d` at the end of build to build image in detached mode `docker compose build -d`
`docker compose up` - run the images
`docker compose down` - 

list in .yml file look like 
```
- thing 1
- thing 2
- thing 2
```

nginx1.dockerfile code

```
FROM nginx
RUN apt update -y

EXPOSE 80

```
`ENV DB_HOST=mongodb://mongodb:27017/posts` - command for creating environment variable in app container to connect to db container (add to dockerfile)