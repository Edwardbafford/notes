
Software for building Linux containers.
- Namespaces to provide isolation
- cgroups to restrict CPU, memory, and disk consumption


# Architecture

**Docker Registry** - stores docker images

**Docker Daemon** 
- pulls docker images from registries 
- creates containers from images
- creates images from Dockerfiles
- pushes images to registries

**Docker Client** - command line utility used to communicate with a docker daemon


# Images

Images are a "blueprint" for creating containers

Images are built in **layers**. Each layer is a version of the image filesystem. These layers can be re-used across many images to save building time and image storing space.

View docker image layers
`docker history IMAGE` 

**Dockerfile** contains the steps to build an image. 

Each step within a Dockerfile is a **directive**

Directives
- `FROM` - base image to build off of
- `RUN` - commands to run on the layer
- `WORKDIR` - define the working directory, applies at runtime and build time
- `ADD` and `COPY`- adds a file from your local machine into the image
- `EXPOSE` - set default port and protocol
- `STOPSIGNAL` -  sets the signal that will be sent to the container when exiting
- `ENTRYPOINT` - command to execute when running the container
	- Has a default
	- Can be overridden
	- Can be extended with `CMD`
- `CMD` - commands to append to the `ENTRYPOINT` command, can be overriden at runtime

Make the entrypoint command as specific as possible for security purposes.

Build an image from a Dockerfile
`docker build IMAGE:VERSION DOCKERFILE_PATH`

Image name structure
`REGISTRY/ACCOUNT/IMAGE:VERSION`

## Multi-stage Builds

Execute build steps in one base image then copy artifacts into a lean and secure second base image.

Execute steps on one base image. Add a name to reference later.
`FROM IMAGE AS NAME`

Add a second base image later in the Dockerfile and copy artifacts into it.
`COPY --from=NAME scr dst`

Using a distroless base image will increase performance, security, and image size. The distroless images lack the basic tools of an OS image.


## Managing Images

Pull from registry into daemon
`docker pull IMAGE`

Remove old images
`docker rmi IMAGE`

Push to registry
`docker login`
`docker push IMAGE`

Remove layers with no image
`docker images prune`

Flatten images (remove layers) for potentially better runtime performance.
`docker export ...`
`docker import ...`




# Running

**Containers** are created from **Images**

`docker run IMAGE:TAG [COMMAND]`
- `-d` runs the image as a detched process
- `--rm` deletes the container after it is stopped, otherwise it must be stopped and deleted
- `-it` work with the container interactively if you execute a command when running container
- `--name` give a name to the container
- `--restart unless-stopped` automatically restarts the container unless it's stopped
- `-p HOST:CONTAINER` maps a host port to a container port
- `--memory 1000M` limit container memory

`docker ps`
See docker containers running

`docker logs CONTAINER_ID`
See the STDOUT/STDERR from the container

`docker stop CONTAINER`
Stops the container

`docker start CONTAINER`
Starts a stopped container

`docker rm CONTAINER`
Deletes a stopped container

## Logging

Docker uses log drivers to export container logs from STDOUT/STDERR to a chosen destination.

Control logging configuration through daemon.json file

