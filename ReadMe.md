# Udemy course: Docker Essentials 


### To pull nginx image using docker

```
docker image pull nginx:latest
```

### Run the pulled image as a container

```
docker container run -itd --name web-server-nginx -p 8080:80 nginx:latest
```
- **itd** : i(nteractive-> keeps standard input open), t(ty-> allocates pseudo terminalfor the container), d(etach-> runs the container in background)
- **name**: assigns a custom human readable name to the container
- **p 8080:80**:  maps host port (8080) to container port (80). allows acces to container via 8080


## Docker basics

### Stages

Dockerfiles -> build, Images -> pull, Containers -> run

### Docker Engine

**Docker Client**, **Docker Host**, **Docker Registry**


**Docker Client**: medium though which we interact with docker. [CLI(docker pull, docker run), API(client.containers.run, client.containers.list)]

**Docker Host**: Machine which actually performs containerization. It runs docker daemon which builds dockerfile to create docker images.[docker daemon, containers, images]

**Docker Registry**: It is the storage for docker images and make it available to others. [images]

### Dockerfile

- A sequential set of instruction for Docker Engine
- Primary way of interacting with Docker
- Each instruction creates a layer
- Layers can be caches and reused by Docker

#### Dockerfile Structure
no extension: for compantibilty with the autobuilder used by docker.

##### Instruction Categories:

1. Fundamental:  
FROM  
ARG (to define arguments used by **FROM** instruction, helps keeping versions under control)

2. Configuration:  
RUN  
ADD | COPY  
ENV

3. Execution:  
CMD  
ENTRYPOINT  
EXPOSE  

## Dockerfile tutorial

### Tutorial 1

Create a Dockerfile: S2/D-1/Dockerfile  

Build the image from this docker file using command:  
```
docker build -t img_from .
```

### Tutorial 2

Create a Dockerfile: S2/D-2/Dockerfile  

Build the image from this docker file using command:  
```
docker build -t img_run-env .
```  

Run the container:  
```
docker run -itd img_from-env --name cont_run-env
```  

Bring the cotainer forward:
```
docker exec -it cont_run-env bash
```

### Tutorial 3

Create a Dockerfile: S2/D-3/Dockerfile  

Build the image from this docker file using command:  
```
docker build -t img_expose .
```  

Run the container:  
```
docker run -itd --rm img_expose --name cont_expose -p 8080:80
```  

### Tutorial 4

Create a Dockerfile: S2/D-4/Dockerfile  

Build the Apache image from this docker file using command:  
```
docker build -t img_apache .
```  

Run the container:  
```
docker run -itd --name cont_apache -p 8080:80 img_apache
```  

This container runs an Apache web server on port 80 and exposes it on the host machine through port 8080.




