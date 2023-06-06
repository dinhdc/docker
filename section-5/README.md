# Topic in this section

- All about images, the building blocks of containers
- What's in an image (and what isn't)
  - App binaries and dependencies
  - Metadata about the image data and how to run the image
  - Offical definition: "An image is an ordered collection of root filesystem changes and the corresponding execution parameters for use within a container run time"
  - Not a complete OS. No kernel, kernel modules
  - Small as a one file (your app binary) like a golang static binary
  - Big as a Ubuntu distro with apt, and Apache, Php, and more installed
- Using Docker Hub registry
- Managing out local image cache

## The Mighty Hub: Using Docker Hub Registry Images

- Basics of Docker Hub
- Find Offical and other good public images
- Download images and basics of image tags

## Images and Their Layers: Discover the Image Cache

- Image layers
- union file system
- ```history``` and ```inspect``` commands
  - ```docker history <image>```
  - ```docker image inspect <image>```
- copy on write

## Image Tagging and Pushing to Docker Hub

- All about image tags
  - ```docker image tag <image> <username>/<image>```
  - ```docker image tag nginx congdinh2k/nginx```
  - ```docker image tag congdinh2k/nginx congdinh2k/nginx:testing```
- How to upload to Docker Hub
  - ```docker image push <username>/<image>```
  - ```docker image tag push congdinh2k/nginx```
  - ```docker image tag push congdinh2k/nginx:testing```
- Image ID vs Tag

## Building Images: The Dockerfile Basics

- Command:
  - ```docker build .```
  - ```docker build -f some-dockerfile```
- Concept:
  1. package manager: ```FROM ubuntu:latest```
  2. environments variable: ```ENV NGINX_VERSION 1.25.0~jessie```
- Sample:
  - Sample 1: custom nginx
    - cd to *dockerfile-sample-1*: ```cd /section-5/sample/dockerfile-sample-1```
    - run build image with docker file: ```docker build -t customnginx .```
  - Sample 2: extending Offical Images
    - cd to *dockerfile-sample-2*: ```cd /section-5/sample/dockerfile-sample-2```
    - run build image with docker file: ```docker build -t nginx-with-html .```
    - run image with command: ```docker container run -p 80:80 --rm nginx-with-html```
    - open your browser and enter ```localhost```
- Prune:
  - ```docker image prune```: clean up just "dangling" images
  - ```docker system prune```: will clean up everything you're not currently using
  - ```docker image prune -a```: which will remove all images you're not using
  - ```docker system df```: see space usage
  