# Containers

Learning notes about container

## 7 keys concepts of Container

    ### Standard Definition of what makes up container image
    - OCI image bundle definition
    
    ### Mechanism to pull container registry to the host
    - <https://github.com/containers/image>

    ### Ability to explode images onto COW files system on disk
    - <https://github.com/containers/storage>

    ### standard mechanism for running a container
    - OCI run time spec

    ### Standard way to setup networking for the container
    - Container networking interface

    ### Tool to monitor container
    - Conmon

## Pods

Is a process on the system that has one or more container inside

## what are container

 it's just using a few features of Linux together to achieve isolation.

## Why we need container

### Bare metal

- Standalone machine without virtualization
- Code is literally executing on the processor with no abstraction
- Cons
  - extremely inflexible,install the physical server takes months
  - keeping the operating system up to date,replacing the components,temperature of the data center
  - Managing your own servers is hard and requires a whole team to do it.

### Virtual Machine
This is adding a layer of abstraction between you and the metal.
Instead of having one instance of Linux.
You'll have multiple guest instances of Linux running inside of a host instance of Linux.
The host operating system offers the VM a certain amount resources and if that VM runs out.