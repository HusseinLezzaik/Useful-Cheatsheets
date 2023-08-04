## Docker Version
```
$ docker --version
$ docker info //  see more information about the Docker daemon, such as the number of containers and images
```

## Image Files
1) .img: use Win32DiskImager to flash the SD card
2) .iso: use Etcher to flash the SD card

## Docker Use Cases
1) Run ros melodic on ubuntu 16.04 with ros kinetic on board
2) Help people use microsoft office specific version on a certain machine

## Tips
- If you're running out of RAM when doing something in docker, and PyTorch is saying you should increase your `shared memory` .. before adding
any configurations to your 'docker run' be sure to include --shm-size + the size you want in mb or gb
- ex:
```
docker run --shm-size=24G -p 8886:8886 --gpus all jupyter-extensions ..
```

## Stopping Containers
- Gracefully stop container
```
$ docker container stop <container id>
```

- Force shutdown of container
```
$ docker container kill <hash>
```

## What is a container
- A container includes:
1) Code
2) Configs
3) Processes
4) Networking
5) Dependencies
6) Operating System
7) Libraries
8) Runtime
9) Environment Variables
- Can reproduce results
- Carves up a computer into sealed computers that run your code
- Gets the code to and from your computers
- Builds these containers for you
- IS a social platform for you to find and share containers, which are different from virtual machines
- A container is a self-contained sealed unit of software, contains everything required to run the code.. includes batteries and operating systems
- A client program named docker
- A server program that manages a Linux System
- A program that builds containers from code
- A container is a running docker image

## Docker under the hood
- Needs a Server Docker Daemon

## Installation
- Docker needs a Linux server to manage
- Many people use a virtual machine on their laptop
- Docker helps run this Linux virtual machine
- IF you have Boot2Docker installed, you most remove it first

## If you want to use GPUS
- You are going to need to use the docker images from Nvidia's website
- Docker File (a list of text that usually defines the dependencies) [Build] -> Docker Image [Run] -> Container
- Docker Registry [Push/Pull] with the Docker Image 

## One-Command Docker Installation
```
$ curl -fsSL https://get.docker.com -o get-docker.sh && chmod +777 get-docker.sh && ./get-docker.sh
```

## The Hello World Docker Image
```
$ docker pull hello-world
$ docker pull ubuntu
$ docker pull ubuntu:18.10
```

## Important Docker Image Commands
```
$ docker image ls
$ docker image ls -a
$ docker image rm <image id>
$ docker image rm $(docker image ls -a -q)
```

## Listing Docker Containers
```
$ docker container ls # list all running docker containers
$ docker container ls -a # list all containers, even those not running
$ docker ps
$ docker images
```

## Stopping Containers
```
$ docker container stop <container id> # gracefully stop container
$ docker container kill <hash> # force shutdown of container
```

## Build Commands
```
$ docker build -t <image_name> .
$ docker container run image_name
$ docker container run -it image_name
```

## Dockerfile basics
```
$ FROM <image> 
```
- example: FROM ubuntu:18.10
```
$ LABEL version="0.1"
$ LABEL description=" Notebook and data (.csv file) to provide a summary / 
			of the total medals won by participating countries / 
			in the 2008 summer Olympics."
$ WORKDIR /data # always use absolute paths, if not specified it will create one by default
$ COPY <src> <dest>
```
- example: COPY . /data
```
$ RUN pip install jupyter
$ RUN pip install pandas
$ RUN pip install matplotlib
```
OR
```
$ RUN pip install jupyter &&/
      pip install pandas &&/
      pip install matplotlib
$ EXPORT <port>
```
- example: EXPOSE 8888
```
$ CMD ["jupyter", "notebook", "--ip=0.0.0.0", :--port=8888", "--no-browser", "--allow-root"] # run jupyter at start
```
- can only have one CMD command, if more than one exists it will run the last one
- CMD tells it what to run at start

## Docker Container Debugging
- Containers are built on top of containers, once you get a bug while building from a docker file you can log into the linux shell machine with the command below using the debugging ID
```
$ docker container run -it 56908d9dce45 /bin/bash 
```

## Uploading Images to Docker Hub
```
$ docker login
>> Username: HusseinLezzaik
>> Password: sample
$ docker image ls 
$ docker push hello-world:latest # latest as a TAG
```

## Remove docker image
```
$ docker image rm -fce # force delete cz kaza image with same ID
```

## Pull Docker Images from Docker Hub
```
$ docker pull <image_name>
$ docker image ls
$ docker container run <image_name>
```

## Docker for Machine Learning - Example
1) Consider the case where your project consists of featurizing code that is fast to run but requires a lot of memory, and the model training code that is slow to run but requires less memory.
- If you run both parts of the code on the same GPU instances, you'll need GPU instances with high memory, which can be very expensive.
- Instead, you can run your featurizing code on CPU instances and the model training code on GPU instances. 
- This means you'll need a container for the featurizing instances and a container for the training instances.

2) Different containers also might be necessary when differnt steps in your pipeline have conflicting dependencies, such as your featurizer code requires Numpy 0.8 but your model requires NumPy 1.0.
- When you have multiple containers with multiple instances, you might need to set up a network for them to communicate and share resources.
- You might also need a container orchestration tool to manage them and maintain high availability. Kubernetes is exactly that.
