# Some of the Docker Key commands

```bash
# list al container
> docker ps -a
# run container in detach mode and put execute command sleep
> docker run --name foobar -d busybox sleep 3600
# killing the container
> docker kill <name|container_id>
# check all images
> docker images
# search images on docker hub
> docker search <name>
# execute command in container
> docker exec -ti centos /bin/bash
# start and stop the container
> docker start|stop <id|name>
# delete a container
> docker rm <id|name>
# check process running on container
> docker top <id>
# stats of container
> docker stats <id> --no-stream
# To check disk usage
> docker system df
# copy file into docker container
> docker cp <file-name> <id>:/tmp
```

## clean up

```bash
> docker system prune
> docker rmi $(docker image -q)
```

## docker cli commands

```bash
# create and run the docker container in detach mode
> docker run -it --detach --name=my:alpine alpine:3.10
# docker attach container
> docker attach <container-id | name>
# check logs for docker container
> docker logs my-alpine
# inspect the docker container
> docker inspect <container-id | name>
# pause the container
> docker pause <container-id | name>
# un pause container
> docker unpause <container-id | name>
# kill all the container
> docker kill $(docker ps -q)
# Information about docker
> docker info
# history of node:12-stretch in docker hub
> docker history node:12-stretch
# check all the processes in a running container
> docker top <container name | id>
# delete all docker container
> docker container prune
# restart container
> docker restart <container id>
```
