# Swarm Basics Features

## Overlay Multi-Host Networking

- Just choose --driver overlay when creating network
- For container-to-container traffic inside a single Swarm
- Optional IPSec (AES) encryption on network creation
- Each service can be connected to multiple networks
  - (e.g. front-end, back-end)

## Routing Mesh

- Routes ingress (incoming) packets for a Service to proper Task
- Spans all nodes in Swarm
- Uses IPVS from Linux Kernel
- Load balances Swarm Services across their Tasks
- Two ways this works:
- Container-to-container in a Overlay network (uses VIP)
- External traffic incoming to published ports (all nodes listen)

## Routing Mesh Cont

- This is stateless load balancing
- This LB is at OSI Layer 3 (TCP), not Layer 4 (DNS)
- Both limitation can be overcome with:
- Nginx or HAProxy LB proxy, or:
- Docker Enterprise Edition, which comes with built-in L4 web
proxy

  - sudo docker network create --driver overlay mydrupal
  - sudo docker network ls
  - sudo docker service create --name psql --network mydrupal -e POSTGRES_PASSWORD=password postgres:14
  - sudo docker service ls
  - sudo docker sevice ps psql
  - sudo docker service ps psql
  - sudo docker container ls
  - sudo docker container logs psql.1.ms7a2zb7zpn47bjgwdy6j5a2e
  - sudo docker service create --name drupal --network mydrupal -p 80:80 drupal:9
  - sudo docker service create --name search --replicas 3 -p 9200:9200 elasticsearch:2

## Stacks: Production Grade Compose

- In 1.13 Docker adds a new layer of abstraction to Swarm called
Stacks
- Stacks accept Compose files as their declarative definition for
services, networks, and volumes
- We use `docker stack deploy` rather then docker service create
- Stacks manages all those objects for us, including overlay network
per stack. Adds stack name to start of their name
- New ``deploy``: key in Compose file. Can't do build:
- Compose now ignores ``deploy``:, Swarm ignores ``build``:
- ```docker compose``` cli not needed on Swarm server
- Example:
  - `sudo docker stack deploy -c example-voting-app-stack.yml voteapp`
  - `sudo docker service ls`
  - ```sudo docker service stop result vote worker db redis```
  - ```sudo docker service rm result vote worker db redis```
  - ```sudo docker stack deploy -c example-voting-app-stack.yml voteapp```
  - ```sudo docker stack```
  - ```sudo docker stack ls```
  - ```sudo docker stack ps voteapp```
  - ```sudo docker container ls```
  - ```sudo docker stack services voteapp```

## Secrets Storage

- Easiest "secure" solution for storing secrets in Swarm
- What is a Secret?
  - Usernames and passwords
  - TLS certificates and keys
  - SSH keys
  - Any data you would prefer not be "on front page of news"
- Supports generic strings or binary content up to 500Kb in size
- Doesn't require apps to be rewritten

## Secrets Storage Cont

- As of Docker 1.13.0 Swarm Raft DB is encrypted on disk
- Only stored on disk on Manager nodes
- Default is Managers and Workers "control plane" is TLS + Mutual
Auth
- Secrets are first stored in Swarm, then assigned to a Service(s)
- Only containers in assigned Service(s) can see them
- They look like files in container but are actually in-memory fs
- ```/run/secrets/<secret_name>``` or ```/run/secrets/
<secret_alias>```
- Local docker-compose can use file-based secrets, but not secure

## Secrets Command

- ```docker secret create```
- ```docker secret inspect```
- ```docker secret ls```
- ```docker secret rm```
- ```--secret``` flag for ```docker service create```
- ```--secret-add``` and ```--secret-rm``` flags for ```docker service update```
