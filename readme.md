

- `docker images` shows all images save
- `docker pull image-name` gets an image
- `docker run image-name` runs the image
- `docker build -t image-name` 
- `docker push image-name`
- `docker run -d -p 2368:2368 ghost`
- `docker ps` and `docker ps -a` check running containers
- `docker stop container-id` stops running container
- `docker start container-id` starts running container
- `docker exec -it container-id bash` To go inside an container e.g. `docker exec -it 407489057d81 bash` equiverlent to ssh into a machine 


# Micro-services
#docker
- Refactoring monolith architecture into smaller chunks

## Agenda
- Micro-services Architecture
- Docker
- Kubernetes (K8)

# Docker

### Login
To link account and terminal use the script bellow:
`docker login`

## Packages
*find* a package from the [docker hub website](https://hub.docker.com/) and run `docker pull` so that it is downloaded and stored on the local machine.
to launch the container, run `docker run <container>`

#### Images
`docker images`
removing 
`docker rmi <image-name>`

## Copying into the docker image directory 
`docker cp <local/file> <docker ps instance>:<pick/a/location/with/name.html`

## Commit
`docker commit <docker ps instance name> <user-name>/<repo-name>[:tags]`
*Hint*: tags can be left empty to become the place holder *:latest*
## Push
After you have finished with the commit, a push can be done
`docker push <username>/<repo-name>[:tags]`
tags like always can be left empty 

### Detached
using the package *ghost* to run in a detached way use the `-d` argument.
`docker run -d -p 2368:2368 ghost`
- We have defined the __ports__ found on the docker hub website.
## Port
`-p <local port>:<docker port>`
### Listing
- `docker ps` and `docker ps -a`
This will show all active containers

### Container interaction
`docker exec -it <container id from docker ps> bash`
This will allow us to explore the contents of the container.
