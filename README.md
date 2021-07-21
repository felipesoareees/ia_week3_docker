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

 *A server* which is a type of long-running program called a daemon process (the dockerd command). The daemon creates and manages Docker objects, such as images, containers, networks, and volumes.
 
 *A REST API* which specifies interfaces that programs can use to talk to the daemon and instruct it what to do.
 
 *A command* line interface (CLI) client (the docker command). The CLI uses the Docker REST API to control or interact with the Docker daemon through scripting or direct CLI commands.

# How Docker is used in Runtime Environment?
Docker is mainly used by Runtime engineers to build images for tests, validations, and debugging. However, all RTE clients use Docker as a container Runtime for their applications, and an RTE engineer must understand Docker to properly comprehend the entire architecture.

# Docker file
 - What is?

Is a file that contains instructions when building an image. It is through it that we provision the desired image. It is at this stage that we define settings such as: from which source this new image will be downloaded, which command will be executed in its respective layers and which command it will execute in the execution process (post-creation)

![image](https://user-images.githubusercontent.com/83301821/126537491-f80f455f-f87e-45e7-a3ac-e0a53e27ee3d.png)

Above, we have some instructions regarding provisioning the image that will be created. The FROM type field defines which image (public or not) it will be sourced, for our case we use a debian. After that, we set some variables and install some packages and at the end we run a command, this will ensure that the container that is run from this new image will run the stress (obviously this Dockerfile is just a demonstration.)

 - How to image tags work?[PRACTICE]

The tag is an identification of the image's versioning. Imagine that you have an image of an application and that it will be necessary for a specific container to make a modification to the docker file. In other words, we can build a new image with the same name, after all it is the same application, but with different tags. In the tags we can define the versioning of our images.

Demonstration:

![image](https://user-images.githubusercontent.com/83301821/126538278-5100880f-db68-4ff2-957e-8e36fcd12ae2.png)

Note that in the image below, we have several images of a application(apache), but with differents tags.

 - How send an image to a registry? [PRACTICE]

# Run a Docker container with  [PRACTICE]:
 - Detached Mode

By default, if we don't specify the -d option the container will run in foreground. Often this is not interesting (foreground use) as we need to ensure that the environment is provisioned even when we are not with the SSH session open. Thus, detached mode when used together with the run ensures that the process will remain up on the machine running in the background.

Usage:

![image](https://user-images.githubusercontent.com/83301821/126412610-5b24ddf4-9fff-4a31-900b-c2a3b7e876fc.png)

And after this, we have:
![image](https://user-images.githubusercontent.com/83301821/126412687-b2fdc6bc-efbc-47a2-a45e-8d55b145f6e2.png)

Note that the container is a docker process active.

 - Port Mapping 

Containers don't have direct access to machine hardware. As we've already talked about, the Docker Daemon is responsible for providing all types of requests (either from the cli or from the container). Thus, the port mapping is done between requests and containers and other layers that may consume resources from the docker. Docker uses port forwarding to define the routes between the incoming and outgoing connections of each of the containers. Through the Net Filter (iptables) the proper routing is done.

![image](https://user-images.githubusercontent.com/83301821/126413168-1dfd554c-2c02-4f8c-acce-a5664f0fe5fe.png)

(avaible in : https://www.gta.ufrj.br/ensino/eel879/trabalhos_v1_2017_2/docker/network.html)

Usage:

![image](https://user-images.githubusercontent.com/83301821/126413361-66e5ecdb-f1d9-4692-a3e7-607dcf4c154a.png)

After this, note:
![image](https://user-images.githubusercontent.com/83301821/126413419-f6e6798c-820a-4fcb-8d2c-59d3393cd15b.png)

There are the parameter 0.0.0.0:5432 > 5432 . The port 5432 external was mapped to 5432 internal. This case, there wasn't PAT (port address translation).

 - Bind Mount

It is used for occasions where the volume directory already exists (also when it is not located in the default docker folder). We can define any directory to be the mount point of the container volume.

Usage:

![image](https://user-images.githubusercontent.com/83301821/126416835-4632d586-1e6c-4857-9827-db266aebc052.png)

With a option type = bind , we choose a source directory to represent a destination directory within the container

After this, we may have the following situation:

![image](https://user-images.githubusercontent.com/83301821/126417168-62da2d49-7370-4823-a59d-3ce1e0c1cb53.png)

After writing to the file inside the container, on the host machine we have the same writing on the filesystem.

 - Volume Mount

Another type of montage is through the volume. Unlike bind, the volume can be managed by *"docker volume [options]"* and the content by default is located in */var/lib/docker/volume/*

Usage:

![image](https://user-images.githubusercontent.com/83301821/126418563-1519fd7c-66ea-479d-9415-a0ea9e202f32.png)

Above we created a volume called db_data and pointed the files from a postgresql container to populate this volume. After running the container with the volume type mount point, the default postgresql files (located in /data) were populated on the previously created volume.
