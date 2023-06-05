# **what we cover**
- ## command: **docker version**
    - ### verified cli can talk to engine
- ## command: **docker info**
    - ### most config values of engine
- ## docker command line structure
    - ### **docker *command* *sub-command* (options)**

## Image vs. Container
- An image is the application we want to run
- A Container is an instance of that image running as a process
- You can have many containers running off the same image

## Docker Command
- **docker  conatiner run**: starts a new container from an image
    - docker container run --publish 80:80 nginx
    - step 1: downloaded image "nginx" from Docker Hub
    - step 2: started a new container from that image
    - step 3: opened port 80 on the host IP
    - step 4: routes that traffic to the container IP, port 80
    - docker container run --publish --detach 80:80 nginx
- **docker  container ls**: list running containers
    - docker container ls
    - docker container stop <container_id>
    - docker container ls -a
    - docker container run --publist port:port --detach --name container_name image
        -  docker container run --publish 80:80 --detach --name webhost nginx
- **docker container logs**: show logs for a specific container
- **docker container top**: process list in one container
- **docker container inspect <container_name>**: details of one container config
- **docker container stats**: performance stats for all containers
- **docker container run -it**: start new container interactively
    - docker container run -it --name proxy nginx bash
    - bash shell: if run with -it, it will give you a terminal inside the running container
- **docker container exec -it**: run additional command in existing container

## Docker Networks
- Review of **docker container run -p**
- For local dev/testing, networks ussually "just work"
- Quick port check with "docker container port *container*"
- Learn concepts of Docket Networking
- Understand how network packets move around Docker