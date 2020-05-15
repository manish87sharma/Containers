# Namespaces

 The concept of namespaces is to limit what processes can see and access certain parts of the system,
 such as other network interfaces or processes.

When a container is started, the container runtime, such as Docker, will create new namespaces to sandbox the process. By running a process in it's own Pid namespace, it will look like it's the only process on the system.

The available namespaces are:

* Mount (mnt)
* Process ID (pid)
* Network (net)
* Interprocess Communication (ipc)
* UTS (hostnames)
* User ID (user)
* Control group (cgroup)
  
```bash
# list all namespace for a process
> ls -lha /proc/$(pgrep redis-server)/ns
```

Namespaces do not restrict access to physical resources such as CPU, memory and disk. That access is metered and restricted by a kernel feature called ‘cgroups’

```bash
> sudo unshare --fork --pid --mount-proc bash
# NSEnter is used to attach processes to existing Namespaces. Useful for debugging purposes.
> sudo nsenter --target $(pgrep redis-server) --mount --uts --ipc --net --pid ps aux
```

With Docker, these namespaces can be shared using the syntax container:<container-name>. For example, the command below will connect nginx to the DB namespace

```bash
# create and run nginx and sharing network name space
> docker run -d --name=web --net=container:db nginx:alpine
# The command below will connect nginx to the DB namespace.
> sudo ls -lha /proc/$(pgrep nginx | tail -n1)/ns | grep net
# same output as both share common name space
> sudo ls -lha /proc/$(pgrep redis-server)/ns | grep net
# install ip command
> sudo yum install net-tools
# execute command in given namespace
> ip netns exec <name> arp
# List all network interfaces
> ip netns exec <name> ip link
# Add Network name space
> ip netns add
# remove network namespace
> ip netns remove
# list network name space
> ip netns list
# display routing and ARP table
> route,arp
```
