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

## How to build a container
1. install [boot2docker](http://boot2docker.io/) and run ```boot2docker up```
2. initialize ```$(boot2docker shellinit)```
3. paste it into **~./bash_profile** for automated initialization
4. build a docker container **docker build -t ${your repo} .*
5. run a docker container **docker run -d -p 80:80 --name static ${your repo}**

6. get ip address **boot2docker ip** and name it to **boot2docker.me** or whatever:) into
`sudo vim /etc/hosts`.

7. make changes to the application and redo **4-5** steps. Also, make sure to stop & delete previous docker process.

8. After docker login, docker push `docker push ${your repo}`

## Testing on Production server
Currently, I am using [Digital Oceans](https://www.digitalocean.com/) as a hosting provider.
I already added a droplet called **docker-test** to check out how it works in production mode.

1. ssh `root@docker.me` and login to Ubuntu (virtual machine)
Previously, I set an **ip address** to **docker.me** for convenience in `/etc/hosts`
2. run public repo you created **docker run -d -p 80:80 --name static ${your repo}** ex) `docker run -d -p 80:80 --
name project saintlee0127/static_nginx`
3. check it out on **docker.me**
