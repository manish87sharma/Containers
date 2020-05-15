# Cgroups

CGroups limit the amount of resources a process can consume.
These cgroups are values defined in particular files within the /proc directory.

One of the properties of Docker is the ability to control memory limits. This is done via a cgroup setting.

By default, containers have no limit on the memory. We can view this via docker stats command.

```bash
# check all cgroup of a process
> cat /proc/$(pgrep redis-server)/cgroup
# list all the available cgroup
> sudo ls /sys/fs/cgroup/
# show cpu stat for a given container
> sudo cat /sys/fs/cgroup/cpu,cpuacct/docker/{conatiner-id}/cpu.shares
# To check the container stats
> docker stats db --no-stream
```

All actions with Linux is done via syscalls. The kernel has 330 system calls that perform operations such as read files, close handles and check access rights. All applications use a combination of these system calls to perform the required operations.

AppArmor is a application defined profile that describes which parts of the system a process can access

```bash
cat /proc/$DBPID/attr/current
```

Seccomp provides the ability to limit which system calls can be made, blocking aspects such as installing Kernel Modules or changing the file permissions.

```bash
# The flag meaning are: 0: disabled 1: strict 2: filtering
> cat /proc/$DBPID/status |grep Seccomp
```

## Capabilities

Capabilities are groupings about what a process or user has permission to do. These Capabilities might cover multiple system calls or actions, such as changing the system time or hostname.
The status file also containers the Capabilities flag. A process can drop as many Capabilities as possible to ensure it's secure.

```bash
# list capabilities for a process
> cat /proc/533/status | grep ^Cap
# The flags are stored as a bitmask that can be decoded with capsh
> capsh --decode=00000000a80425fb
```
