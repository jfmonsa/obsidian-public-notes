---
mocs:
    - "[[public-notes/03-resources/devops.moc.md|DevOps & Cloud]]"
tags:
    - dev/devops
---

- Written in Go
- Docker is a software platform that allows you to create, deploy, and manage applications in containers.
- enables you to separate your applications from your infrastructure
- Containers are standardized units of software that include everything needed to run an application: code, libraries, dependencies, and configurations.
- Docker ensures portability and consistency of applications across different environments (development, testing, production).
## Main Concepts
### Docker File
+ A Dockerfile is a text file that contains a series of instructions to build a Docker image.
#### Keywords
+ `FROM`: Points to an existing docker image to extend
+ `WORKDIR`: creates a working directory and cds into it
+ `RUN`: use a linux package manager to install dependencies
+ `COPY`: copy files from our local directory to container
+ `ENV` to set environment vars
+ `EXPOSE <port>`: to the container to be able to handle external network traffic
+ `CMD`: command you want to run wen starting the container
+ `.dockerignore` file, used to avoid certain files goes to your docker image
#### Caching Layers
+ Caching in docker works by layers. Each instruction in Dockerfile will create a layer that can potentially be cached.
### Image
+ A Docker image is an immutable template that contains the set of instructions to create a container.
+ Images are stored in repositories, such as Docker Hub.
+ are **inmutable** so e.g. when you edit your code you have to create a new docker image
+ **Versionamiento**: Las imágenes se versionan mediante etiquetas (tags). Si necesitas una actualización o cambio, creas una nueva versión de la imagen y la etiquetas en consecuencia.
### Container
+ solve performance issues of virtual machines
	+ **virtualization**: run a virtual os in the host machine, consumes hardware resources from its host, and it's manage by a sofware called ==Hypervisor== (e.g VMWare, Virtual Box)
#### Docker Containers
- A container is a runnable instance of a Docker image.
- Containers are lightweight and run in isolation from each other and the host system
- Are stateless
### Orchestration
+ Tools like Docker docker-compose, Swarm and Kubernetes manage the orchestration of containers in a cluster.
+ They handle the deployment, scaling, and operation of containerized applications.
# Commands
+ `docker images`
+ `docker pull <image name>`
+ `docker ps` watch running containers
+  `docker ps -a`  list all containers including stopped ones
+ `docker rmi <id_de_la_imagen>` delete downloaded docker image
+ `docker rm <id_del_contenedor>` delete stopped container
+ `docker stop <id_del_contenedor>`
+ `docker start <id_del_contenedor>`
+ `docker build -t <nombre:tag> <ruta_del_dockerfile>`
+ `docker exec -it <id container> <command>` run a command in an active docker container
+ `docker exec -it <id container> /bin/bash` access bash terminal in the executing container
# Postgrest docker
Option 1
```
docker pull postgres:alpine
docker run --name postgres-0 -e POSTGRES_PASSWORD=password -d -p 5432:5432 postgres:alpine
```

Option 2
Usando docker-compose.yml
```
services:
    database:
        image: postgres:16.2
        environment:
            POSTGRES_DB: ${LOCALDB_NAME}
            POSTGRES_USER: ${LOCALDB_USER}
            POSTGRES_PASSWORD: ${LOCALDB_PASSWORD}
        ports:
            - "5432:${LOCALDB_PORT}"
        volumes:
            - database:/var/lib/postgresql/data
volumes:
    database:
```

## psql
```
psql -U postgres #log in as postgres user
\du
CREATE DATABASE <DB NAME>
\l # list databases
\c <DB NAME> # connect to a db
\d # show relations of db