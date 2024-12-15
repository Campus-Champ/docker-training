# docker-training

Docker CLI commands:

* docker ps

Lists all running Docker containers. 
	If you want to see all containers (not just running), use `docker ps -a`

* docker pull [image name]:[tag]

Downloads a Docker image from Docker Hub

* docker images

Lists all Docker images that you have locally

* docker run [image name]:[tag]

run a Docker container from a Docker image. 
You can specify the image either by its name or ID.
** DETACH

docker run -d [image name]:[tag]
runs in detached mode, eg, doesn't hijack your terminal
run will pull the image from docker hub if it isn't found locally
** PORT BINDING

docker run -d -p [local port]:[container port] [image name]:[tag]
** NAME THE CONTAINER

docker run --name [given name] -d -p [local port]:[container port] [image name]:[tag]

* docker logs [container name | container id]

Fetches the logs of a container. 
You can specify the container either by its name or ID.

* docker stop [container name | container id]

Stops a running Docker container. 
You can specify the container either by its name or ID.

* docker start [container name | container id]

starts an existing container

* docker rm [container name | container id]

Deletes a Docker container. 
You can specify the container either by its name or ID.

* docker rmi [container name | container id]

Removes a Docker image. 
You can specify the image either by its name or ID.

* docker images

--------
DOCKER FILE
the file from which an image is built
--------

FROM
Sets the base image for subsequent instructions. 
A valid Dockerfile must start with a `FROM` instruction.
Example: `FROM ubuntu:18.04`

COPY
Copies files or directories from `<src>` 
and adds them to the filesystem of the container at the path `<dest>`
Example: `COPY . /app/`
the trailing slask `/` means create this folder if it doesn't exist
Example: `COPY package.json /app/`
Example: `COPY src /app/`

WORKDIR
Sets the working directory 
for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY` and `ADD` instructions that follow it in the Dockerfile.
Example: `WORKDIR /app`

RUN
Executes any commands in a shell/terminal inside the container environment
The commands add a new layer on top of the current image and commit the results. 
The resulting committed image will be used for the next step in the Dockerfile.
Example: `RUN npm install`
Example: `RUN apt-get update && apt-get install -y python3`

CMD
Provides defaults for an executing container. 
These can include an executable, or they can omit the executable, in which case you must specify an `ENTRYPOINT` command.
Example: `CMD ["executable","param1","param2"]`
Example: `CMD ["node","server.js"]`

--------
Build a DOCKER IMAGE from a DOCKER FILE
--------

docker build -t [name:tag] 
Builds a Docker image from a Dockerfile in the current directory. 
The `-t` option lets you specify a name and tag for the image.

docker exec -it [container_id] command
Runs a command in a running container. 
The `-it` options make the session interactive so you can interact with the command. 
You can specify the container either by its name or ID.

docker-compose up
Starts all services defined in a `docker-compose.yml` file

docker-compose down
Stops and removes all services defined in a `docker-compose.yml` file.
