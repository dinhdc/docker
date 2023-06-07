# The Multi-Container Tool

## Docker Compose

- configure relationships between containers
- save our docker container run settings in easy-to-read file
- create one-liner developer environment startups
- comprised of 2 separate but related things
- yaml-formatted file that describes out solution options for:
    1. containers
    2. networks
    3. volumes
- a cli tool ```docker compose``` used for local dev/test automation with those YAML files

## docker-compose.yml

- compose YAML format has it's own versions: 1,2,2.1,3,3.1
- YAML file can be used with ```docker compose``` command for local docker automation
- with ```docker``` directly in production with Swarm (as of v1.13)
- ```docker compose --help```
- ```docker-compose.yml``` is default filename, but any can be used with ```docker compose -f``` command

## Basic Commands

- ```docker compose up```: setup volumes and networks and start all containers
- ```docker compose down```: stop all containers and remove cont/vol/net

## Adding Image Building to Compose File

- ```docker compose build```
