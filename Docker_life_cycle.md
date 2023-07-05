# Docker life cycle

### The complete lifecycle of a docker container revolves around five phases:

* Create phase
* Running phase
* Paused phase/unpause phase
* Stopped phase
* Killed phase

1. Create phase
### In the create phase, a docker container is created from a docker image.

```
docker create --name <name-of-container> <docker-image-name>
```
2. Running phase
In the running phase, the docker container starts executing the commands mentioned in the image. To run a docker container, use the docker run command.
```
docker run <container-id>
```

OR
```
docker run <container-name>
```

The docker run command creates a container if it is not present. In this case, the creation of the container can be skipped.

3. Paused phase/Unpause phase
Paused phase:
In the paused phase, the current executing command in the docker container is paused. Use the docker pause command to pause a running container.
```
docker pause container <container-id or container-name>
```

Note: docker pause pauses all the processes in the container. It sends the SIGSTOP signal to pause the processes in the container.

Unpause phase
In the unpause phase, the paused container resumes executing the commands once it is unpaused.

Use the docker unpause command to resume a paused container.

Then, Docker sends the SIGCONT signal to resume the process.
```
docker unpause <container-id or container-name>
```

4. Stop phase
In the stop phase, the container’s main process is shutdown gracefully. Docker sends SIGTERM for graceful shutdown, and if needed, SIGKILL, to kill the container’s main process.

Use the docker stop command to stop a container.
```
docker stop <container-id or container-name>
```

Restarting a docker container would translate to docker stop, then docker run, i.e., stop and run phases.

5. Kill phase
In the kill phase, the container’s main processes are shutdown abruptly. Docker sends a SIGKILL signal to kill the container’s main process.
```
docker kill <container-id or container-name>
```
