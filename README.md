# ia_week3_docker

- Description : This repository has the challenge of week three. It explain the containers linux and docker tools and  docker concepts.

## The schedule this project is:

# What is a linux container?
Linux containers are technologies that allow you to package and isolate applications with their entire runtime environment—all of the files necessary to run. Meaning Linux containers are portable and consistent as they move from development, to testing, and finally to production. (avaible in: https://www.redhat.com/en/topics/containers/whats-a-linux-container and https://www.redhat.com/en/topics/containers)

The architecture of linux containers offers us the use of an application in different environments, which has different architectures and yet we can guarantee usability for each one of them. This is different from virtualization in that there is no more than one kernel running applications. All resources are consumed by the OS of a single machine, however, to guarantee the facility in question, it is necessary to pre-configure an environment in which we can guarantee that the application will work correctly.

Thus, we have:
![image](https://user-images.githubusercontent.com/83301821/126407332-d4ca1ec9-7985-42bc-876d-f4896be9ed03.png)
(avaiable in: https://www.redhat.com/cms/managed-files/virtualization-vs-containers.png  acess day 20/07 it 20:23 o'clock GMT-3)

Note that the container architecture has neither the hypervisor layer nor the guest operating system. Communication with the OS host is done directly through the runtime file support.

![image](https://user-images.githubusercontent.com/83301821/126408633-451f6b19-a4c0-49a9-877a-9c886319f978.png)

With the container, we can avoid situations like the image above, because we can guarantee that the application will work on all OS, just that the environment setup is done correctly.

# What is a Docker?

- What is?

It is an open source project that uses container technology for operating system virtualization. As we talked about containers in the previous topic, docker emerged as a tool that uses container technology to provide solutions that ensure usability in all environments.

The most succinct and coherent definition (in my opinion is): Docker is an open source platform for building, deploying, and managing containerized applications. *(avaible in : https://www.ibm.com/cloud/learn/docker )

- What is its high-level architecture (Docker Daemon)?
This is a client-server application with these major components:

![image](https://user-images.githubusercontent.com/83301821/126408917-5f346daa-72e1-4ea3-8c0d-0946f9c85893.png)
(avaible in: https://medium.com/@hsienwei/a-high-level-overview-of-docker-888d8556e187) 

 A server which is a type of long-running program called a daemon process (the dockerd command). The daemon creates and manages Docker objects, such as images, containers, networks, and volumes.
 
 A REST API which specifies interfaces that programs can use to talk to the daemon and instruct it what to do.
 
 A command line interface (CLI) client (the docker command). The CLI uses the Docker REST API to control or interact with the Docker daemon through scripting or direct CLI commands.

# How Docker is used in Runtime Environment?
Docker is mainly used by Runtime engineers to build images for tests, validations, and debugging. However, all RTE clients use Docker as a container Runtime for their applications, and an RTE engineer must understand Docker to properly comprehend the entire architecture.

# Docker file
 - What is?
 - How to image tags work?[PRACTICE]
 - How send an image to a registry? [PRACTICE]

# Run a Docker container with  [PRACTICE]:
 - Detached Mode
 - Port Mapping 
 - Bind Mount
 - Volume Mount
