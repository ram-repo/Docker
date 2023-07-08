## Docker volume

commonly used volume types in Docker:

#### Bind Mounts:
A bind mount is a reference to a specific directory on the host machine that is mounted into a container. It allows sharing files or directories between the host and the container. Bind mounts are created using the -v or --mount flag when starting a container.

#### Named Volumes:
Named volumes are managed by Docker and have a specific location within the Docker host's file system. They provide an abstraction layer that separates the container from the host, making it easier to manage and move containers between different environments. Named volumes can be created using the docker volume create command or by specifying the volume in a docker-compose.yml file.

#### Tmpfs Mounts: 
Tmpfs mounts are stored in the host system's memory and are suitable for temporary data that doesn't need to be persisted across container restarts. They are useful for scenarios where you need a high-performance, in-memory file system for storing temporary files.

#### Volume Drivers: 
Docker also allows the use of volume drivers to provide additional functionality and integration with external storage systems. Volume drivers enable the use of specialized storage platforms like NFS, GlusterFS, Ceph, and more. These drivers extend the capabilities of Docker volumes to support distributed or networked storage solutions.


### Create a named volume:
```docker volume create <volume_name>```

### List volumes:
```docker volume ls```

### Inspect a volume:
```docker volume inspect <volume_name>```

### Remove a volume:
```docker volume rm <volume_name>```

### Start a container with a volume:
```docker run -v <volume_name>:<container_path> <image_name>```
This command mounts an existing volume into a container at the specified container path.

### Start a container with a bind mount:
``` docker run -v <host_path>:<container_path> <image_name>```
This command mounts a directory from the host machine into the container.

### Start a container with a tmpfs mount:
``` docker run --tmpfs <container_path> <image_name>```

### This command creates a temporary in-memory file system within the container.

### use a volume driver:
```docker run -v <volume_name>:<container_path> --volume-driver=<driver_name> <image_name> ```







## docker volume create: Creates a named volume.
```docker volume create myvolume```

## docker volume ls: Lists all available volumes.
```docker volume ls```

## docker volume inspect: Displays detailed information about a volume.

```docker volume inspect myvolume```

## docker volume rm: Removes a volume.
```docker volume rm myvolume```

## docker run -v: Mounts a volume or bind mount when starting a container.

```
docker run -v myvolume:/path/in/container myimage
docker run -v /host/path:/path/in/container myimage
```
