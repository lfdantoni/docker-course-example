# Docker example

It is a simple example using docker and docker compose from https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/ course (modules 1-5)

## Commands

### Dockerfile

- WORKDIR /usr/app -> specify the work directory, every file system command is going to apply in that folder
  - when we run a container, we can rerun it but we can't override the startup command. A container create is like an snapshot which we can't modify it

### Docker
- docker run <image_name>
  - create a new container in order to run and start a new image instance, that command is the same as running docker create <image_name> + docker start <container_id>
  - <startup_command> -> override the image startup command
- docker run -it <image_name> sh
  - it is similar to docker exec -it <container_id> sh command
  - it is going to create and run a container but a bash console opened by default without any startup command executed
- docker run -p <port_outside>:<port_inside_image> <image_name>
  - to specify the port mapping of incoming requests
- docker ps -> all the containers which are running
  - --all -> the containers which were or are running 
- docker create <image_name> -> create a new container
  - <startup_command> -> it is going to override the image startup command
- docker start <container_id> -> start the container by executing the image startup command
  - -a  -> to attach to the container and showing the logs
- docker system prune -> delete all created containers
- docker logs <container_id> -> it will show the container logs
- docker stop <container_id> 
  - it is going to stop the container with a SIGTERM signal
  - if after 10 seconds it doesn't response, it is going to execute docker kill command
- docker kill <container_id> 
  - it is going to kill the container process with a SIGKILL signal
  - no matter what is happening in the container, it is going to finish it
- docker exec -it <container_id> <command>
  - it is going to exec other command into a running container
  - -it -> it is going to allow to attach the container input channel and format it
- docker exec -it <container_id> sh
  - it is going to open a shell command into a running container in order to execute multiple commands inside of it.
  - close with Ctrl+D
  - SEE docker run -it <image_name> sh command
- docker build . -> create an image based a dockerfile 
- docker build -t <docker_account_id>/<tag_name>:<version> .
  - <docker_account_id> -> your docker hub id
  - <tag_name> -> the tag name of your image
  - <version> -> it is optional the image version, it could be latest



### Docker Compose

- docker-compose up
- docker-compose up --build 
  - to rebuild images
- docker-compose up -d
  - to run in backgrond
- docker-compose down 
  - to stop all the containers
- docker-compose ps
- similar as docker ps, but it only run into docker-compose.yml's directory

