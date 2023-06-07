# **what we cover**

## command: **docker version**

    verified cli can talk to engine

## command: **docker info**

    most config values of engine

## docker command line structure

    **docker *command* *sub-command* (options)**

## Image vs. Container

- An image is the application we want to run
- A Container is an instance of that image running as a process
- You can have many containers running off the same image

## Docker Command

- ```docker  conatiner run```: starts a new container from an image
  - ```docker container run --publish 80:80 nginx```
  - step 1: downloaded image "nginx" from Docker Hub
  - step 2: started a new container from that image
  - step 3: opened port 80 on the host IP
  - step 4: routes that traffic to the container IP, port 80
  - docker container run --publish --detach 80:80 nginx
- ```docker  container ls```: list running containers
  - ```docker container ls```
  - ```docker container stop <container>```
  - ```docker container ls -a```
  - ```docker container run --publist port:port --detach --name container_name image```
    - ```docker container run --publish 80:80 --detach --name webhost nginx```
- ```docker container logs```: show logs for a specific container
- ```docker container top```: process list in one container
- ```docker container inspect <container>```: details of one container config
- ```docker container stats```: performance stats for all containers
- ```docker container run -it```: start new container interactively
  - docker container run -it --name proxy nginx bash
  - bash shell: if run with -it, it will give you a terminal inside the running container
- ```docker container exec -it```: run additional command in existing container

## Docker Networks

1. Introduce Docker Networks Concept

   - Review of ```docker container run -p```
   - For local dev/testing, networks ussually "just work"
   - Quick port check with "docker container port *container*"
   - Learn concepts of Docket Networking
   - Understand how network packets move around Docker
   - Some command using:
     - docker container run -p 80:80 --name webhost -d nginx
     - docker container inspect --format '{{ .NetworkSettings.IPAddress }}'  webhost

2. CLI Management in Docker Networks

   - Show networks ```docker network ls```
   - Inspect a network ```docker network inspect```
      - ```docker container inspect --format '{{ .NetworkSettings.IPAddress }}'  <container>```
      - ```docker container inspect --format '{{ .NetworkSettings.IPAddress }}'  webhost```
   - Create a network ```docker network create --driver```
      - ```docker network create my_app_network```
      - ```docker container run -d --name new_nginx --network my_app_network nginx```
   - Attach a network to container ```docker network connect```
      - ```docker network connect <network> <container>```
   - Deattach a network from container ```docker network disconnect```
      - ```docker network disconnect <network> <container>```

3. DNS in Docker Networks

   - Unsderstand how DNS is the key to easy inter-container comms
   - See how it works by default with custom networks
   - Learn how to use ```--link``` to enable DNS on default bridge network
     - ```docker container run -d --name my_new_nginx --network my_app_network nginx```
