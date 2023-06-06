# Manage Multiple Containers

- create nginx:
  - ```docker container run -p 80:80 -d --name my_nginx nginx```
- create httpd:
  - ```docker container run -p 8080:80 -d --name my_httpd httpd```
- create mysql:
  - ```docker container run -p 3306:3306 -e MYSQL_RANDOM_ROOT_PASSWORD=yes -d --name my_mysql mysql```
