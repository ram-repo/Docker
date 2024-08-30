
# Docker

## 1. Introduction to Docker
Docker is a platform for developing, shipping, and running applications inside lightweight, portable containers.

### Key Concepts:
- **Containers**: Isolated environments that run applications.
- **Images**: Snapshots of a container's filesystem and configuration.
- **Dockerfile**: Script to build Docker images.
- **Docker Hub**: Repository for Docker images.

## 2. Installing Docker
- **Official Documentation**: [Docker Install Guide](https://docs.docker.com/get-docker/)
- Docker is available for various platforms: Windows, macOS, and Linux. Follow the official instructions to install Docker Desktop (for Windows and macOS) or Docker Engine (for Linux).

## 3. Basic Docker Commands
- `docker run`: Start a new container from an image.
- `docker ps`: List running containers.
- `docker images`: List available images.
- `docker build`: Build an image from a Dockerfile.
- `docker pull`: Download an image from a registry (e.g., Docker Hub).
- `docker push`: Upload an image to a registry.

## 4. Creating a Simple Docker Application
- **Step 1**: Write a simple application (e.g., a Python Flask app).
- **Step 2**: Create a `Dockerfile` for the app:
    ```Dockerfile
    # Use an official Python runtime as a parent image
    FROM python:3.8-slim

    # Set the working directory in the container
    WORKDIR /app

    # Copy the current directory contents into the container at /app
    COPY . /app

    # Install any needed packages specified in requirements.txt
    RUN pip install --no-cache-dir -r requirements.txt

    # Make port 80 available to the world outside this container
    EXPOSE 80

    # Run app.py when the container launches
    CMD ["python", "app.py"]
    ```
- **Step 3**: Build the Docker image:
    ```bash
    docker build -t my-flask-app .
    ```
- **Step 4**: Run the container:
    ```bash
    docker run -p 4000:80 my-flask-app
    ```

## 5. Understanding Docker Images and Containers
- **Images**: Immutable, read-only layers. Built from Dockerfiles.
- **Containers**: Running instances of images, with a writable layer on top.

## 6. Networking in Docker
- **Bridge Network**: Default network for containers on a single host.
- **Host Network**: Containers share the host's networking namespace.
- **Custom Network**: Define your own network settings for better isolation and control.

## 7. Data Persistence with Volumes
- Use Docker Volumes to persist data:
    ```bash
    docker volume create my_volume
    docker run -v my_volume:/data my-flask-app
    ```

## 8. Docker Compose
- Define and run multi-container applications:
    - **docker-compose.yml** Example:
        ```yaml
        version: '3'
        services:
          web:
            image: my-flask-app
            ports:
              - "4000:80"
          db:
            image: postgres
        ```
- Commands:
    - `docker-compose up`: Start all services defined in the `docker-compose.yml`.
    - `docker-compose down`: Stop and remove services.

## 9. Best Practices
- **Keep Images Small**: Use smaller base images (e.g., `alpine`).
- **Multi-Stage Builds**: Reduce image size by separating build and runtime environments.
- **Minimize Layers**: Each command in a Dockerfile adds a layer. Combine commands where possible.

## 10. Further Reading and Resources
- [Docker Documentation](https://docs.docker.com/): Official Docker documentation.
- [Play with Docker](https://labs.play-with-docker.com/): An online environment to learn Docker interactively.
- [Docker Getting Started Guide](https://docs.docker.com/get-started/): A guide to start with Docker.
- [Docker Cheat Sheet](https://dockerlabs.collabnix.com/docker/cheatsheet/): Handy reference for Docker commands.
