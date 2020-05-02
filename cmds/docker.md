# Docker CheatSheet

Dangling means not associated with a container.

## Overview
- [List](#list)
    - [Images](#list-images)
    - [Container](#list-containers)
    - [Volumes](#list-volumes)
- [Build](#build)
- [Run](#run)
- [Remove](#remove)
    - [All](#remove-all)
    - [Images](#remove-images)
    - [Container](#remove-containers)
    - [Volumes](#remove-volumes)

<br>

# List
## List Images
- All
```bash
docker images -a
```

- Dangling 
```bash
docker images -f dangling=true
```

## List Container
- All
```bash
docker ps -a
```

- Exited
```bash
docker ps -a -f status=exited
```

## List Volumes
- All
```bash
docker volume ls
```

- Dangling
```
docker volume ls -f dangling=true
```

<br>


# Build
Build an image from the Dockerfile in current directory and tag the image
```bash
docker build -t myimage:1.0 .
```

<br>


# Run
### Interactive

### Headless
- Using image myimage 1.0
- Name the running container “web”
- Expose port 5000 externally, mapped to port 80 inside the container.
```bash
docker container run --name web -p 5000:80 myimage:1.0
```

### Connect to headless container
```bash
docker exec -it $CONTAINER_NAME /bin/bash
```

### See the last 100 logs
Print the last 100 lines of a container’s logs docker container
```bash
docker container logs --tail 100 web
```

<br>

# Remove

## Remove All

- Dangling resources — images, containers, volumes, and networks
```bash
docker system prune
```

- I Said All
```bash
docker system prune -a
```

## Remove Images
- Single
```bash
docker rmi $IMAGE_ID
```

- Dangling
```bash
docker images purge
```

- All
```bash
docker rmi $(docker images -a -q)
```


## Remove Containers
- Single
```bash
docker rm $CONTAINER_ID
```

- Exited
```bash
docker rm $(docker ps -a -f status=exited -q)
```


## Remove Volumes
- Single
```bash
docker volume rm $VOLUME_NAME
```

- Dangling
```bash
docker volume prune
```