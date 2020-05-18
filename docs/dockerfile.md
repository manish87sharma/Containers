# Docker File

```bash
# Creating a container with docker file -t, --tag
> docker build -t <name>:version
# running docker container with tini aka --init means node can handle SIGTERM such as ctrl+c
# This uses a package called tini to handle shutdown signal for you
> docker run --init <name>
# To expose a port from docker to host machine
> docker run --init --publish 3000:3000 --rm <name>
#
```

## Note

- don't run container as root user
- Most node images come with user node,always use the user which don't have root permission

COPY and ADD do very similar things with a few key differences. ADD can also accept, in addition to local files, URLs to download things off the Internet and it will also automatically unzip any tar files it downloads or adds. COPY will just copy local files. Use COPY unless you need to unzip something or are downloading something.

## sample docker file

```yaml
FROM node:12-stretch

USER node

WORKDIR /home/node/code

COPY --chown=node:node index.js .mmnm

CMD ["node", "index.js"]
```
