# Docker
Docker is a virtualization platform that allows developers to easily create, deploy, and run applications in containers. Containers are lightweight, portable, and self-sufficient environments that can run applications consistently across different computing environments.

![alt text](../../assets/docker-vm.png)

**Containers** - consist of layers of linux base image, application image with configuration and dependencies, and a thin read-write layer on top.

Traditional applications often require complex setups and dependencies, which can lead to issues when deploying across different environments.

* Setup hardware
* Install operating system (e.g., Linux, Windows)
* Install necessary software and dependencies (e.g., databases, libraries)
* Configure the application to work with the installed software
* Install the application itself

Docker solves this problem by packaging applications and their dependencies into a single container that can run on any system with Docker installed.

Deployment steps using Docker:
1. **Create a Dockerfile**: A Dockerfile is a text file that contains instructions on how to build a Docker image. It specifies the base image, the application code, and any dependencies needed to run the application.
2. * **Build the Docker image**: Use the `docker build` command to create a Docker image from the Dockerfile. The Docker image is an executable application artifact that contains everything needed to run the application e.g. the code, runtime, libraries etc.
3. **Run the Docker container**: Use the `docker run` command to start a container from the built image. The container will run the application as an instance of the image in an isolated environment, ensuring consistency across different systems.

![alt text](../assets/docker.png)

## Dockerfile
A Dockerfile is a text file that contains instructions for building a Docker image. It specifies the base image, the application code, and any dependencies needed to run the application. Here is an example of a simple Dockerfile:

```Dockerfile
# Use an official Node.js runtime as the base image
# Must begin with FROM instruction - to specify the base image
FROM node:25.8

# Set the working directory in the container
COPY package.json /app/
COPY server.js /app/

WORKDIR /app

# RUN instruction to execute commands in a shell inside the container during the build process. It is used to install dependencies, set up the environment, and perform other tasks needed to prepare the image for running the application.
RUN npm install

# CMD instruction to specify the default command to run when starting a container from the image. It is used to define the command that will be executed when the container starts, such as running the application or starting a server. Only one CMD instruction is allowed in a Dockerfile, and if multiple CMD instructions are present, only the last one will take effect.
CMD ["node", "server.js"]
```



**Docker Registry** - A Docker registry is a collection of repositories for storing and distributing Docker images. The most popular public registry is Docker Hub, which allows users to share and access a wide variety of Docker images. Organizations can also set up private registries to store and manage their own images securely.

**Docker Repository** - A Docker repository is a collection of related Docker images, typically organized by application or project. Each repository can contain multiple images, which are tagged with different versions or variants of the application.

**Image Versions** - Docker images can have multiple versions, which are typically tagged with a version number or a descriptive name. This allows developers to manage different versions of their applications and easily switch between them when needed.

**Port Mapping** - When running a Docker container, you can specify port mapping to allow communication between the container running in an isolated Docker network and the host machine. This is done using the `-p` flag in the `docker run` command, which maps a port on the host to a port in the container. For example, `docker run -p 8080:80 <image_name>:<tag>` would map port 8080 on the host to port 80 in the container, allowing you to access the application running in the container through the host's port 8080.

## Docker Basic Commands
- `docker images`: List all Docker images available on the local machine.
- `docker ps`: List all running Docker containers.
- `docker ps -a`: List all Docker containers, including those that are stopped.

- `docker build -t <image_name>:<tag> .`: Build a Docker image from a Dockerfile in the current directory, tagging it with a specified name and tag.
- `mvn spring-boot:build-image -Dspring-boot.build-image.imageName=<image_name>:<tag>`: Build a Docker image for a Spring Boot application using the Spring Boot Maven plugin, specifying the image name and tag.

- `docker pull <image_name>:<tag>`: Pull a Docker image from a registry.


- `docker run <image_name>:<tag>`: Run a Docker container from a specified image. If the image is not available locally, Docker will automatically pull it from the registry before running the container.
- `docker run -d <image_name>:<tag>`: Run a Docker container in detached mode (in the background). 
- `docker run --name <container_name> <image_name>:<tag>`: Run a Docker container with a specified name.
- `docker run -p <host_port>:<container_port> <image_name>:<tag>`: Run a Docker container with port mapping, allowing access to the application running in the container through the specified host port.
- `docker start <container_id>`: Start a stopped Docker container.
- `docker stop <container_id>`: Stop a running Docker container.
- `docker rm <container_id>`: Remove a stopped Docker container.

- `docker tag <image_name>:<tag> <new_image_name>:<new_tag>`: Tag an existing Docker image with a new name and tag, allowing you to manage different versions of your images.
- `docker push <image_name>:<tag>`: Push a Docker image to a registry, making it available for others to pull and use. 
- Image naming in registry `registry_domain/image_name:tag` 
  - `docker push accountId.dkr.ecr.eu-north-1.amazonaws.com/ultron-app:latest` image name needs `accountId.dkr.ecr.eu-north-1.amazonaws.com` to act as the registry domain
  - `docker push sakusanpuwan/ultron-app:2.0` image name needs `sakusanpuwan` to act as the namespace

## Docker Compose
Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to define the Docker commands used in services, networks, and volumes needed for your application in a single `docker-compose.yml` file. With Docker Compose, you can easily start, stop, and manage all the containers in your application with a single command.

- `docker-compose -f <docker-compose.yml> up`: Start all the services defined in the `docker-compose.yml` file, creating and starting the containers as needed including networks.
- `docker-compose -f <docker-compose.yml> down`: Stop and remove all the containers, networks, and volumes defined in the `docker-compose.yml` file.

## Docker Network
When running multiple Docker containers, you can create an isolated Docker network to allow communication between the containers. This is done using the `docker network create` command, which creates a new network that containers can be connected to. Containers connected to the same network can communicate with each other using their container names as hostnames.

- `docker network ls`: List all Docker networks available on the local machine.
- `docker network create <network_name>`: Create a new Docker network with a specified name

## Docker Container
`docker exec -it <container_id> /bin/bash` / `docker exec -it <container_id> /bin/sh` : Execute a command inside a running Docker container, allowing you to interact with the container's filesystem and processes. The `-it` flag enables interactive mode and allocates a pseudo-TTY, while `/bin/bash` starts a Bash shell inside the container.

## Private Docker Registry
A private Docker registry is a self-hosted service that allows you to store and manage your own Docker images securely. It provides a way to share images within an organization or team without relying on public registries like Docker Hub. 

AWS ECR (Elastic Container Registry) is a fully managed Docker container registry provided by Amazon Web Services. It allows you to store, manage, and deploy Docker container images securely and at scale. 

1. Create a new repository in AWS ECR to store your Docker images. You can do this using the AWS Management Console or the AWS CLI. For example, using the AWS CLI:
`aws ecr create-repository --repository-name ultron-app --region eu-north-1`
2. Retrieve an authentication token and authenticate your Docker client to your registry. Use the AWS CLI:
`aws ecr get-login-password --region eu-north-1 | docker login --username AWS --password-stdin 625250728892.dkr.ecr.eu-north-1.amazonaws.com`
Note: If you receive an error using the AWS CLI, make sure that you have the latest version of the AWS CLI and Docker installed.
3. Build your Docker image using the following command. 
`docker build -t ultron-app .`
4. After the build completes, tag your image so you can push the image to this repository:
`docker tag ultron-app:latest 625250728892.dkr.ecr.eu-north-1.amazonaws.com/ultron-app:latest`
5. Run the following command to push this image to your newly created AWS repository:
`docker push 625250728892.dkr.ecr.eu-north-1.amazonaws.com/ultron-app:latest`

---  
## Ultron Example
- `docker build -t ultron:1.0 .`: Build a Docker image for the Ultron application from the Dockerfile in the current directory, tagging it as `ultron:1.0`.
- `docker run -d -p 8080:9000 ultron:1.0`: Run a Docker container for the Ultron application in detached mode, mapping port 8080 on the host to port 9000 in the container.