# Named Volumes

- ```docker volume create psql```
- ```docker run -d --name psql1 -e POSTGRES_PASSWORD=mypassword -v psql:/var/lib/postgresql/data postgres:15.1```
- ```docker logs psql1```
- ```docker stop psql1```
- ```docker run -d --name psql2 -e POSTGRES_PASSWORD=mypassword -v psql:/var/lib/postgresql/data postgres:15.2```
- ```docker logs psql2```
- ```docker stop psql2```
