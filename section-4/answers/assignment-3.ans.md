# DNS Round Robin Test

- Answers:
  - ```docker network create dude```
  - ```docker container run -d --net dude --net-alias search elasticsearch:2```
  - ```docker container run -d --net dude --net-alias search elasticsearch:2```
  - ```docker container run --rm --net dude alpine nslookup search```
  - ```docker container run --rm --net dude centos curl -s search:9200```
