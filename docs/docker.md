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
