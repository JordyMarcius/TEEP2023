:::warning
# <center><i class="fa fa-edit"></i> Docker & Kubernetes</center>
:::

###### tags: `Docker` `Kubernetes` `TEEP` `Internship`

:::success
**Learning Objective:**

The study objectives were to:
- Understand about docker
- Understand about kubernetes
:::

[TOC]

# I. Docker

## I.I. Introduction
The main problem while running or testing an application is the application code that has been created by a developer doesn't always work in the other system due to the ==difference in computer environments.== There are two solutions for this problem, i.e., **Virtual Machine** and **Docker**.

**Virtual Machine** is a virtual environment that functions as a virtual computer with its own operating system (OS), memory, network interface, and storage used to run programs and deploy applications. One physical machine or computer can run one or more virtual machines separately from each other.

**Docker** is an open-source software platform that provides capabilities to run and deploy an application in a loosely isolated environment called a **container**. 

## I.II. Why use docker?

![image alt](https://download.huawei.com/mdl/image/download?uuid=7e915df1792845a3baaa388c94fc3934)
*img src: https://info.support.huawei.com/info-finder/encyclopedia/en/Docker+Container.html*

Virtual machine can solve the problem, but docker will be the better solution. ==Docker is more lightweight than virtual machine== because it doesn't own operating system (OS) in each container, but can provide the same functionality as virtual machine. Docker container runs in a host machine (physical computer), but the process in a container cannot affect other containers because the **docker engine** or **container manager** can isolate one container from others.

==Another advantages of docker:==
- Docker containers occupy less space
- Short boot time
- Easy to set up 

## I.III. Architecture
![image alt](https://docs.docker.com/engine/images/architecture.svg)
*img src: https://docs.docker.com/get-started/overview/*

- **Docker client** ==used by users to interact with docker.== Docker client is a terminal application that contains docker commands. These commands uses docker API to communicate with one or more docker daemon.
- **Docker daemon** is a part of docker host. It ==listens for docker API request and manages docker objects,== such as containers and images. 
- **Docker host**
	- **Images** is ==an immutable files that contains source code, libraries, and other dependencies needed for an application to run.== Docker images can be created using *Dockerfile*. Docker images used to build docker container. You can find a lot of open source images for free in the [Docker Hub](https://hub.docker.com/).
	- **Containers** is ==a runnable instance of an image.== The docker host can run multiple containers from the same images. The containers can be crated or managed using docker API. By default, a container is isolated from other containers and its host machine. 
- **Docker registry** is ==used to stores docker images.== So, the images can be used by multiple docker server.

## I.IV. Basic Docker Commands

|Command|Description|
| ---------- | -------- |
|```docker version```|Show the docker version information.|
|```docker search```|Search docker images from Docker Hub.|
|```docker pull```|Download an image from Docker Hub (by default) or another registry.|
|```docker images```|List all the images by repository, tag, image ID, created, and size|
|```docker ps```|List all the containers by ID, image, command, created, status, ports, and names|
|```docker push```|Upload an image to the Docker Hub or another registry.|
|```docker create```|Creates a new container from the specified image without starting it.|
|```docker start```|Start one or more stopped containers.|
|```docker stop```|Stop one or more running containers.|
|```docker run```|Creates and run a new container from an image.|
|```docker build```|Build an image from a Dockerfile.|
|```docker rm```|Remove one or more containers|
|```docker restart```|Restart one or more containers|



# II. Kubernetes

## II.I. Introduction
**Kubernetes** (also known as **K8s**) is an open-source system for automating deployment, scaling, and management of ==containerized== applications. Kubernetes provides framework to run distributed systems resiliently.

Kubernetes features:
- **Storage orchestration**. Kubernetes allows users to automatically mount a storage system, such as local storages, cloud, etc.
- **Automated rollouts and rollbacks**. Kubernetes can be used to remove existing container, then create a new one and adopt all resources from previous container automatically.
- **Automatic bin packing**. Kubernetes can manage CPU and RAM consumption for each container to use computer resources efficiently.
- **Self-healing**. Kubernetes can restarts containers that fail, replaces and reschedules containers when nodes die.

## II.II. Architecture
![image alt](https://d33wubrfki0l68.cloudfront.net/2475489eaf20163ec0f54ddc1d92aa8d4c87c96b/e7c81/images/docs/components-of-kubernetes.svg)
*img src: https://kubernetes.io/docs/concepts/overview/components/*

- **Kubernetes Master / Control Panel** responsible to make global decisions aboud the cluster, detecting and responding to cluster events.
	- **kube-apiserver** exposes the kubernetes API that used to interacts with all of kubernetes cluster components. 
	- **etcd** acts as a database to store kubernetes cluster data.
	- **kube-scheduler** is responsible to watchs the running applications and make requests to Node to start an application.
	- **kube-controller-manager (c-m)** is responsible to control kubernetes cluster process.
	- **cloud-controller-manager (c-c-m)** is responsible to control the interactions with cloud provider.
- **Kubernetes Nodes** is a worker machine in kubernetes. Node components run on every node, maintaining running pods and providing the kubernetes runtime environment. ==A pod represent a set of running containers in kubernetes cluster.==
	- **kubelet** is an agent that runs on each node. It makes sure that containers are running in a pod.
	- **kube-proxy** maintains network rules on nodes.
	- **container runtime** is the software that is responsible for running containers.

:::success
**References:**
- [Docker docummentation](https://docs.docker.com/get-started/overview/)
- [What is Kubernetes](https://cloud.google.com/learn/what-is-kubernetes) 
- [Kubernetes docummentation](https://kubernetes.io/)
:::