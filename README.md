# docker
Learning Docker in depth

## Basic Docker Commands:

```
  $ docker run <image>
  $ docker start <name|id>
  $ docker stop <name|id>
  $ docker ps [-a include stopped containers]
  $ docker rm <name|id>
```

## Setup

1. go to ~/etc/hosts ```sudo vim /etc/hosts```
2. add '''your own docker IP address'''
3. reset password (got a hashed password from Docker.)
4. create a docker hub account or sign into docker ```docker login```
5. test run ```docker run tutum/hello-world```. This does not work because it is exposing a port to
   Docker daemond but Docker Daemond is not exposing to the world
6. So run ```docker run -p 8080:80 tutum/hello-world``` and check ```docker ps -a```
7. run three instances and use load balancer (later)
`docker run --name -d --name web1 -p 8081:80 tutum/hello-world`
`docker run --name -d --name web2 -p 8082:80 tutum/hello-world`
`docker run --name -d --name web3 -p 8083:80 tutum/hello-world`
```
$ docker start web1
$ docker stop web1
$ docker stop web2
$ docker stop web3
$ docker rm web1 etc...
```
## References
https://www.youtube.com/watch?v=K6WER0oI-qs
