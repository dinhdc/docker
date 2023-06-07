# Container Lifetime && Persistent Data

## Overview

- Defining the problem of persistent data
  - Containers are *ussually* immutable and ephemeral
  - "immutable infrastructure": only re-deploy containers, never change
  - This is the idea scenario, but what about databases, or unique data?
  - Docker give us features to ensure these "separation of concerns", is known as "persistent data"
  - Two ways: Volumes and Bind Mounts
  - Volumes: make special localtion outside of container UFS
  - Bind Mounts: link container path to host path
- Key concepts with containers: immutable, ephemeral
- Learning and using Data Volumes
- Learning and using Bind Mounts

## Persistent Data: Volumes

- Command:
  - Volume name:
    - ```docker container run -d --name <container_name> [options] -v <volume_name>:<path> image```
    - ```docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysq```
  - Volume create:
    - ```docker volume create```
  - Volume inspect:
    - ```docker volume inspect <volume>```

## Persistent Data: Bind Mounts

- Overview:
  - Maps a host file or directory to a container file or directory
  - Basically just two locations pointing to the same file(s)
  - Again, skip UFS, and host files overwrite any in container
  - Can't use in Dockerfile, must be at ```container run```
    - ```... run -v /Users/admin/stuff:/path/container``` (mac/linux)
    - ```... run -v //c/Users/admin/stuff:/path/container``` (windows)

- Command:
  - Volume name:
    - ```docker container run -d --name <container_name> [options] -v <volume_name>:<path> image```
    - ```docker container run -d --name mysql -e MYSQL_ALLOW_EMPTY_PASSWORD=True -v mysql-db:/var/lib/mysql mysq```
  - Volume create:
    - ```docker volume create```
  - Volume inspect:
    - ```docker volume inspect <volume>```
  
  - Example:
    - cd to ```dockerfile-sample-2```
    - ```docker container run -d --name nginx -p 80:80 -v $(pwd):/usr/share/nginx/html nginx```
