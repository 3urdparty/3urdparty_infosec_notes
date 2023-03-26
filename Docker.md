Open-source platform for automating the deployment of applications as self-contained units called containers. Uses layered filesystem and resource isolation features to provide flexibility and portability.

The Docker engine and specific Docker images are needed to run a container. These can be obtained from the Docker Hub, a repository of pre-made images, or created by the user. The Docker Hub is a cloud-based registry for software repositories or a library for Docker images. It is divided into a public and a private area. The public area allows users to upload and share images with the community. It also contains official images from the Docker development team and established open-source projects. Images uploaded to a private area of the registry are not publicly accessible. They can be shared within a company or with teams and acquaintances.

Creating a Docker image is done by creating a Dockerfile, which contains all the instructions the Docker engine needs to create the container. We can use Docker containers as our “file hosting” server when transferring specific files to our target systems. Therefore, we must create a Dockerfile based on Ubuntu 22.04 with Apache and SSH server running. With this, we can use scp to transfer files to the docker image, and Apache allows us to host files and use tools like curl, wget, and others on the target system to download the required files. Such a Dockerfile could look like the following:

```bash
# Use the latest Ubuntu 22.04 LTS as the base image
FROM ubuntu:22.04

# Update the package repository and install the required packages
RUN apt-get update && \
    apt-get install -y \
        apache2 \
        openssh-server \
        && \
    rm -rf /var/lib/apt/lists/*

# Create a new user called "student"
RUN useradd -m docker-user && \
    echo "docker-user:password" | chpasswd

# Give the htb-student user full access to the Apache and SSH services
RUN chown -R docker-user:docker-user /var/www/html && \
    chown -R docker-user:docker-user /var/run/apache2 && \
    chown -R docker-user:docker-user /var/log/apache2 && \
    chown -R docker-user:docker-user /var/lock/apache2 && \
    usermod -aG sudo docker-user && \
    echo "docker-user ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Expose the required ports
EXPOSE 22 80

# Start the SSH and Apache services
CMD service ssh start && /usr/sbin/apache2ctl -D FOREGROUND
```

Then to build it from the previous `dockerfile`:
```bash
docker build -t FS_docker
```

Docker Run - Syntax
```bash
docker run -d -p <host port>:<docker port> <docker container name>
```

Docker Run
```bash
docker run -d -p 8022:22 -p 8080:80 -d FS_docker
```

Docker management
When managing docker containers, Docker provides a comprehensive suite of tools that enable us to easily create, deploy and manage containers.

# Commands
| command          | Description                 |
| ---------------- | --------------------------- |
| `docker pd`      | List all running containers |
| `docker stop`    | stop a running container    |
| `docker start`   | Start a stopped container   |
| `docker restart` | Restart a running container |
| `docker rm`      | Remove a container          |
| `docker rmi`     | Remove a container          |
| `docker rmi`     | Remove a docker image       |
| `docker logs`    | View the logs of a container |                            |

It is worth noting that these commands, used in Docker, can be combined with various options to provide additional functionality. For example, we can specify which ports to expose, mount volumes, or set environment variables. This allows us to customize our Docker containers to suit our needs and requirements. When working with Docker images, it's important to note that any changes made to an existing image are not permanent. Instead, we need to create a new image that inherits from the original and includes the desired changes.

This is done by creating a new Dockerfile that starts with the FROM statement, which specifies the base image, and then adds the necessary commands to make the desired changes. Once the Dockerfile is created, we can use the docker build command to build the new image, tagging it with a unique name to help identify it. This process ensures that the original image remains intact while allowing us to create a new image with the desired changes.

It is important to note that Docker containers are designed to be immutable, meaning that any changes made to a container during runtime are lost when the container is stopped. Therefore, it is recommended to use container orchestration tools such as Docker Compose or Kubernetes to manage and scale containers in a production environment.

