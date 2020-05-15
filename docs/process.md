# processes

## Containers are just normal Linux Processes with additional configuration applied

```bash
> docker run -d --name=db redis:alpine
# list the process
> ps aux | grep redis-server
# Display the running processes of a container
> docker top db
#list all sub process, options compact,show pids, use ASCII line drawing character
> pstree -c -p -A $(pgrep dockerd)
```

## dockerd is the docker daemon

```bash
# Start Docker this way, it runs in the foreground and sends its logs directly to your terminal.
> dockerd
# command help
> dockerd --help
# common example
> dockerd --debug \
  --tls=true \
  --tlscert=/var/docker/server.pem \
  --tlskey=/var/docker/serverkey.pem \
  --host tcp://192.168.59.3:2376

# default daemon directory is
- /var/lib/docker on Linux.
- C:\ProgramData\docker on Windows.
```

The configuration for each process is defined within the /proc directory. If you know the process ID, then you can identify the configuration directory.Each process has it's own configuration and security settings defined within different files.

```bash
# read the environment file for redis process
> sudo cat /proc/$(pgrep redis-server)/environ
# Same command as above
> docker exec -it db env
# list all the namespaces
> sudo ls -lha /proc/$(pgrep redis-server)/ns/

```

### references

    - [exercise] (https://www.katacoda.com/courses/container-runtimes/what-is-a-container)
    - [pgrep] (https://linuxize.com/post/pgrep-command-in-linux/)
