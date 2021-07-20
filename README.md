# ia_week3_docker

- Description : This repository has the challenge of week three. It explain the docker tools and  docker concepts.

## The schedule this project is:

# What is a linux container?
Linux containers are technologies that allow you to package and isolate applications with their entire runtime environment—all of the files necessary to run. Meaning Linux containers are portable and consistent as they move from development, to testing, and finally to production. (avaible in: https://www.redhat.com/en/topics/containers/whats-a-linux-container and https://www.redhat.com/en/topics/containers)

The architecture of linux containers offers us the use of an application in different environments, which has different architectures and yet we can guarantee usability for each one of them. This is different from virtualization in that there is no more than one kernel running applications. All resources are consumed by the OS of a single machine, however, to guarantee the facility in question, it is necessary to pre-configure an environment in which we can guarantee that the application will work correctly.

Thus, we have:
![image](https://user-images.githubusercontent.com/83301821/126407332-d4ca1ec9-7985-42bc-876d-f4896be9ed03.png)
(avaiable in: https://www.redhat.com/cms/managed-files/virtualization-vs-containers.png  acess day 20/07 it 20:23 o'clock GMT-3)

Note that the container architecture has neither the hypervisor layer nor the guest operating system. Communication with the OS host is done directly through the runtime file support.

# What is a Docker?

- What is?
- What is its high-level architecture (Docker Daemon)?

# How Docker is used in Runtime Environment?

# Docker file
 - What is?
 - How to image tags work?
 - How send an image to a registry?

# Run a Docker container with:
 - Detached Mode
 - Port Mapping 
 - Bind Mount
 - Volume Mount

# Hands On:

- Install Docker
- Practice with options of the run (detached,port mapping, volumes and bind.
