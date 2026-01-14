Docker Different Concepts
=========================

### 1. Introduction to Docker

    Docker is a platform for building, packaging, shipping, and running applications in lightweight, portable containers. Containers make it easy to ensure consistent environments across development, testing, and production.

### 2. Images

    Images are read-only templates used to create containers.

    Key points:

    1. Built from a Dockerfile.

    2. Layered architecture enables caching and fast builds.

    3. Can be pulled from registries such as Docker Hub.

    4. Immutable once created.

    Common commands:
    ```
    $ docker build -t app .
    $ docker pull ubuntu
    $ docker images

### 3. Containers

    Containers are running instances of images.

    Key points:

    1. Lightweight and isolated.

    2. Start instantly because they share the host OS kernel.

    3. Ephemeral by design (data is lost unless stored in volumes).

    Common commands:
    
    $ docker run -it ubuntu bash
    $ docker ps
    $ docker stop <id>
    $ docker rm <id>

### 4. Dockerfile

    A Dockerfile contains instructions to build an image.

    Example:

    Dockerfile
    ----------
    FROM node:18
    WORKDIR /app
    COPY . .
    RUN npm install
    CMD ["node", "server.js"]

    
    Common instructions:

    FROM

    COPY

    RUN

    CMD

    ENTRYPOINT

    EXPOSE

### 5. Registries

    A registry is a repository for storing and sharing images.

    Examples:

    Docker Hub (default)

    GitHub Container Registry

    AWS ECR

    Google Artifact Registry

    Commands:
    
        $ docker login
        $ docker push username/app
        $ docker pull username/app

### 6. Volumes

    Volumes allow persistent storage outside containers.

    Use cases:

    Databases

    Logs

    Shared state

    Commands:
    
        $ docker volume create data
        $ docker run -v data:/var/lib/mysql mysql
        $ docker volume ls

### 7. Networks

    Docker provides networking for container-to-container or container-to-host communication.

    Types:

    - bridge (default)

    - host

    - none

    - overlay (for Swarm)

    Commands:
    
        $ docker network ls
        $ docker network create mynetwork
        $ docker run --network=mynetwork app

### 8. Docker Compose

    Docker Compose is used to manage multi-container applications using a docker-compose.yml file.

    Example:

    docker-compose.yml
    ------------------
    version: "3.8"
    services:
        web:
            image: nginx
        db:
            image: postgres
        volumes:
            - pgdata:/var/lib/postgresql/data

        volumes:
            pgdata:


    Commands:
    
        $ docker compose up
        $ docker compose down

### 9. Docker Daemon & CLI
    
    Docker Daemon (dockerd)

    Background service managing containers, images, networks, and volumes.

    Docker CLI (docker)

    Command-line tool used to communicate with the daemon.

### 10. Container Isolation Concepts

    Docker uses Linux kernel features:

    1. Namespaces

    2. Process isolation

    3. Network isolation

    4. Mount points

    5. Control Groups (cgroups)

    6. Resource limits (CPU, RAM)

    7. Union File System

    8. Image layer management

### 11. Docker Swarm (Orchestration)

    Swarm provides clustering and scheduling.

    Features:

    - Multi-node orchestration

    - Service scaling

    - Rolling updates

        Commands:
            
            $ docker swarm init
            $ docker service create --replicas 3 nginx

### 12. Kubernetes (Relation to Docker)

    Docker can act as a container runtime under Kubernetes, though it is often replaced with containerd.

    Key concepts:

        1. Pods

        2. Deployments

        3. Services

        4. Ingress

    Kubernetes manages containers at scale, while Docker runs individual containers.

### 13. Best Practices

    Keep Docker images small.

    Use .dockerignore.

    1. Avoid running as root inside containers.

    2. Use multi-stage builds.

Tag images properly.
