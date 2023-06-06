# DNS Round Robin Test

- Requirements:
  - Know how to use ```-it``` to get shell in container
  - Understand basics of what a Linux distribution is like Ubuntu and CentOS
  - Understand basics of DNS records
- Assignment:
  - Create a new virtual network (defaul bridge driver)
  - Create two containers from ```elasticsearch``` image
  - Research and use ```-network-alias search``` when creating them to give them an additional DNS name to respond to
  - Run ```alpine nslookup search``` with ```--net``` to see the two containers list for the same DNS name
  - Run ```centos curl -s search:9200``` with ```--net``` multiple times util you see both "name" fields show
