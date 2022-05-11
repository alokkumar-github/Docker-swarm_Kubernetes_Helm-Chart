https://www.containiq.com/post/popular-kubernetes-distributions
supervisord-vs-systemd
# Docker-swarm-AND-Kubernetes
Shortcut keys to this is ALT+SHIFT+N -> select JUnit Test Case (or hit J 3 times) 
Basic
: docker version
: docker -v
: docker info
: docker --help
ex.    docker images --help
: docker login
————————————
Images
: docker images
: docker pull
: docker rmi
————————————
Containers
: docker ps
: docker run
: docker start
: docker stop
————————————
System
: docker stats
: docker system df
: docker system prune

Today we will learn :

1. What are images
2. How to pull image
3. How to run a container using an image
4. Basic Commands

TIPS & TRICKS


What are Images
Docker Images are templates used to create Docker containers
Container is a running instance of image

Where are Images Stored
Registries (e.g. docker hub)
Can be stored locally or remote

: docker images --help
: docker pull image
: docker images
: docker images -q
: docker images -f “dangling=false”
: docker images -f “dangling=false” -q

: docker run image
: docker rmi image
: docker rmi -f image

: docker inspect
: docker history imageName



Today we will learn :

1. What are Containers
2. How to create Containers
3. How to start / stop Containers
4. Basic Commands

TIPS & TRICKS


What are Containers:
Containers are running instances of Docker Images


COMMANDS
: docker ps
: docker run ImageName
: docker start ContainerName/ID
: docker stop ContainerName/ID

: docker pause ContainerName/ID
: docker unpause  ContainerName/ID

: docker top ContainerName/ID
: docker stats ContainerName/ID

: docker attach ContainerName/ID

: docker kill ContainerName/ID
: docker rm ContainerName/ID

: docker history ImageName/ID


References:
https://www.google.co.in/search?rlz=1...

https://docs.docker.com/engine/refere...
_____________________________________________________

Notes
https://www.youtube.com/watch?v=wi-MGFhrad0&list=PLhW3qG5bs-L99pQsZ74f-LC-tOEsBp2rK&index=1

A container image is a lightweight, stand-alone, executable package of a piece of software that includes everything needed to run it: code, runtime, system tools, system libraries, settings.

Features of Containers:

Are lightweight

Fewer resources are used

Booting of containers is very fast

Can start, stop, kill, remove containers easily and quickly

Operating System resources can be shared within Docker



Containers run on the same machine sharing the same Operating system Kernel, this makes it faster

You can use the command
docker container create
to create a container in stopped state



Today we will learn :

1. How to start Jenkins on Docker Container
2. Start and Stop Jenkins Container
3. How to set Jenkins home on Docker Volume and Host Machine



: docker pull jenkins

: docker run -p 8080:8080 -p 50000:50000 jenkins

: docker run --name MyJenkins -p 8080:8080 -p 50000:50000 -v /Users/raghav/Desktop/Jenkins_Home:/var/jenkins_home jenkins

: docker run --name MyJenkins2 -p 9090:8080 -p 50000:50000 -v /Users/raghav/Desktop/Jenkins_Home:/var/jenkins_home jenkins

: docker volume create myjenkins
: docker volume ls
: docker volume inspect myjenkins

: docker run --name MyJenkins3 -p 9090:8080 -p 50000:50000 -v myjenkins:/var/jenkins_home jenkins

: docker inspect MyJenkins3


References
https://hub.docker.com/


Today we will learn :

1. What is Dockerfile
2. How to create Dockerfile
3. How to build image from Dockerfile
4. Basic Commands

TIPS & TRICKS

Dockerfile : 
A text file with instructions to build image
Automation of Docker Image Creation

FROM
RUN
CMD


Step 1 : Create a file named Dockerfile

Step 2 : Add instructions in Dockerfile

Step 3 : Build dockerfile to create image

Step 4 : Run image to create container



COMMANDS
: docker build 
: docker build -t ImageName:Tag directoryOfDocekrfile

: docker run image

Today we will learn :

1. What | Why - Docker Compose
2. How to install
3. How to create docker compose file
4. How to use docker compose file to create services
5. Basic Commands

TIPS


Docker compose
: tool for defining & running multi-container docker applications
: use yaml files to configure application services (docker-compose.yml)
: can start all services with a single command : docker compose up
: can stop all services with a single command : docker compose down
: can scale up selected services when required


Step 1 : install docker compose
   (already installed on windows and mac with docker)
   docker-compose -v
   
   2 Ways

   1.  https://github.com/docker/compose/rel...

   2. Using PIP
    pip install -U docker-compose

Step 2 : Create docker compose file at any location on your system
   docker-compose.yml

Step 3 : Check the validity of file by command
    docker-compose config

Step 4 : Run docker-compose.yml file by command
   docker-compose up -d

Steps 5 : Bring down application by command
   docker-compose down

TIPS
How to scale services

—scale
docker-compose up -d --scale database=4
 


References:
https://hub.docker.com

https://github.com/docker/compose/rel...

https://docs.docker.com/compose/compo...

https://www.google.co.in/search?q=mic...

Today we will learn:

1. What are Volumes
2. How to create / list / delete volumes
3. How to attach volume to a container
4. How to share volume among containers
5. What are bind mounts ( Bind Mount: a file or direcory on host machine is mounted in a container)
Volumes are the preferred mechanism for persisting data generated by and used by Docker containers


: docker volume  //get information
: docker volume create
: docker volume ls
: docker volume inspect
: docker volume rm
: docker volume prune


Use of Volumes
===========
Decoupling container from storage
Share volume (storage/data) among different containers
Attach volume to container
On deleting container volume does not delete



Commands
docker run --name MyJenkins1 -v myvol1:/var/jenkins_home -p 8080:8080 -p 50000:50000 jenkins
docker run --name MyJenkins2 -v myvol1:/var/jenkins_home -p 9090:8080 -p 60000:50000 jenkins
ocker run --name MyJenkins3 -v /Users/raghav/Desktop/Jenkins_Home:/var/jenkins_home -p 9191:8080 -p 40000:50000 jenkins

References
https://hub.docker.com/_/jenkins/
https://docs.docker.com/storage/volumes/



NOTES

By default all files created inside a container are stored on a writable container layer

The data doesn’t persist when that container is no longer running

A container’s writable layer is tightly coupled to the host machine where the container is running. You can’t easily move the data somewhere else.

Docker has two options for containers to store files in the host machine
so that the files are persisted even after the container stops

VOLUMES  and  BIND MOUNTS

Volumes are stored in a part of the host filesystem which is managed by Docker

Non-Docker processes should not modify this part of the filesystem

Bind mounts may be stored anywhere on the host system

Non-Docker processes on the Docker host or a Docker container can modify them at any time

In Bind Mounts, the file or directory is referenced by its full path on the host machine. 


Volumes are the best way to persist data in Docker

volumes are managed by Docker and are isolated from the core functionality of the host machine

A given volume can be mounted into multiple containers simultaneously.

When no running container is using a volume, the volume is still available to Docker and is not removed automatically. You can remove unused volumes using docker volume prune.

When you mount a volume, it may be named or anonymous. 

Anonymous volumes are not given an explicit name when they are first mounted into a container

Volumes also support the use of volume drivers, which allow you to store your data on remote hosts or cloud providers, among other possibilities.


Today we will learn :

1. What is Docker Swarm
2. Why to use it
3. How to create and manage Docker Swarm
4. Create service on docker swarm
5. Scaling services up and down
6. Features/Helpful Tips



A swarm is a group of machines that are running Docker and joined into a cluster 



Docker Swarm is a tool for Container Orchestration


Let’s take an example

You have 100 containers

You need to do 
- Health check on every container
- Ensure all containers are up on every system
- Scaling the containers up or down depending on the load
- Adding updates/changes to all the containers

Orchestration - managing and controlling multiple docker containers as a single service
Tools available - Docker Swarm, Kubernetes, Apache Mesos



Pre-requisites
1. Docker 1.13 or higher
2. Docker Machine (pre installed for Docker for Windows and Docker for Mac)https://docs.docker.com/machine/insta...
https://docs.docker.com/get-started/p...





Step 1 :  Create Docker machines (to act as nodes for Docker Swarm)   Create one machine as manager and others as workers
    docker-machine create --driver hyperv manager1    docker-machine create --driver virtualbox manager1

   docker-machine:Error with pre-create check: “exit status 126”
   https://stackoverflow.com/questions/3...
   brew cask install virtualbox;

   Create one manager machine
   and other worker machines


Step 2 :  Check machine created successfully
    docker-machine ls
    docker-machine ip manager1


Step 3 :  SSH (connect) to docker machine
    docker-machine ssh manager1


Step 4 :  Initialize Docker Swarm    docker swarm init --advertise-addr MANAGER_IP
    docker node ls
    (this command will work only in swarm manager and not in worker)


Step 5 :  Join workers in the swarm
    Get command for joining as worker
    In manager node run command
    docker swarm join-token worker
    This will give command to join swarm as worker

    docker swarm join-token manager
    This will give command to join swarm as manager

    SSH into worker node (machine) and run command to join swarm as worker
   
    In Manager Run command - docker node ls to verify worker is registered and is ready
  
    Do this for all worker machines


Step 6 :  On manager run standard docker commands
    docker info
    check the swarm section 
    no of manager, nodes etc

    Now check docker swarm command options 
    docker swarm 


Step 7 :  Run containers on Docker Swarm
    docker service create --replicas 3 -p 80:80 --name serviceName nginx

    Check the status:
    docker service ls
    docker service ps serviceName
   
    Check the service running on all nodes
    Check on the browser by giving ip for all nodes


Step 8 :  Scale service up and down
   On manager node 
   docker service scale serviceName=2
 

Inspecting Nodes (this command can run only on manager node)
docker node inspect nodename
docker node inspect self
docker node inspect worker1


Step 9 : Shutdown node
   docker node update --availability drain worker1


Step 10 :  Update service
   docker service update --image imagename:version web
   docker service update --image nginx:1.14.0 serviceName


Step 11 :  Remove service
   docker service rm serviceName


docker swarm leave : to leave the swarm
docker-machine stop machineName : to stop the machine
docker-machine rm machineName : to remove the machine


REFERENCES:
https://docs.docker.com/get-started/p...
https://rominirani.com/docker-swarm-t...

https://www.rapidvaluesolutions.com/kubernetes-versus-docker-swarm-which-one-to-use/



FAQs & Helpful Tips:

A swarm is a group of machines that are running Docker and joined into a cluster

A cluster is managed by swarm manager

The machines in a swarm can be physical or virtual. After joining a swarm, they are referred to as nodes

Swarm managers are the only machines in a swarm that can execute your commands, or authorise other machines to join the swarm as workers

Workers are just there to provide capacity and do not have the authority to tell any other machine what it can and cannot do

you can have a node join as a worker or as a manager. At any point in time, there is only one LEADER and the other manager nodes will be as backup in case the current LEADER opts out

Kubernaties or minions
--------------------------------
master node is responsible for sceduling , provisioning , controlling and exposing api to the cleint. is resposible for managing cluster. it monitor the helgth check of nodes., it shows the information abt the members of cluster and the configuration inside the master .  k8s master is resposible for mananging the entire clusters , it coordinate all the activites inside the cluster and comunicate with the worker nodes to keep k8s and yours application running.

more master node for high avaiblity and fault tolerance.

currently k8s supports 5k worker node(node) per cluster

worker nodes is nothing but virual box, virtual machine or physical server running within the data center or VM in cloud. these are the workhorses of kubernatise cluster , they expose compute n/w & storage resources to the application ,so all these nodes joined together to form a cluster which provide fault tolerence and replication .

pos is basically a scheduling unit in k8s.  each pod contain one or more containers, we interact & manage container through pod.

inside a cluster - inside a worker node(s) - pod(s) (inside a pod ) - container(s) (dependent container for a container 

once install k8s . 4 components ( api server, scheduler , controll manager(node controller ,replication controller, service account and token controller . these controllers are reposible for overall health of entire clusters. it ensure all the node are running always and correct no of pod are running as mention in config ) , etcd ( is a distributed key -value lightweight database use to store current cluster stat at any point of time , this is single source of truth for all the nodes , all the components and the master that are forming k8s cluster. we can query, 

1. api server , it is kind of gatekeeper for the entire clusters , if you want to create , update , delete api objects , we have to go through this api server , it validate & configure Api objects such as pods ,services , replication controller , deployment. and it is responsible for exposing various apis. how to interact with this api using tool cube cytia

2. scheduler is resposible for pysically scheduling pods across multiple nodes , so depending upon the constrainsts that you maintioned in configuation file scheduler schedule these pods accordingly for example CPU as 1 core, memory is 10 gig, disk type is ssd and other containt, that you may want to declare in the artifact so once we pass the artifact to the api server scheduler will look for appropriate node that meet this cretaria and will schedule a pod accordingly.


there are 2 other components require to communicate with k8s master and they are cudelet(primary node agent that run on each worker node inside the cluster , it primary object is to look at the spec that was submitted to api server on the k8s master and ensure the container describe in the pod spec is running and healthy ) and queue proxy 

cluster--- group of server or other resources that act as a single server.
In an automatic cluster, When node 1 fails, automatically node 2,  takes over and communication goes on, that's fine.But my question is, how does the node 2 know, that node 1 has failed . In between each nodes, there would be a heartbeat links (private links [there is a dedicated line between both servers called a heartbeat so that the second node knows when the first node fails.﻿]) connected to it. which monitors each nodes alive or not in the cluster, if any nodes not getting response from other nodes,  cluster software will start running the servicegroups in the running node.

there are two way of cluster. automaic & manual.
4 major type of cluster - High Availibility (active-passive) , load balancing(active-active) , high performance, storage cluster.


in k8s  every think is object like deployment , service , pod etc  

k8s service and deployment
--------------------------------------
how to deploy application inside these pods. any deployment running inside k8s is call workload. workload are running pod inside k8s.
service or deployment which is deployed in k8s - workload. 

label selector -- 
replicaset -- 

references:::::::::::::::


references:::::::::::::::


https://github.com/justmeandopensource/kubernetes/blob/master/docs/install-cluster.md

https://www.youtube.com/watch?v=UWg3ORRRF60

https://www.youtube.com/watch?v=UhSoTq0H-JY&list=PLYliwzTugkt3_8H2JPTUfzQ6NpsEzF41K&index=1

https://www.learnitguide.net/2018/08/what-is-kubernetes-learn-kubernetes.html

https://www.youtube.com/watch?v=jgmdY73RF6w&list=PLMPZQTftRCS8Pp4wiiUruly5ODScvAwcQ

https://www.youtube.com/watch?v=DsHcfoRyDsM&list=PLTyWtrsGknYdHLSdZz9fW0cMnpZny3UPL

https://www.youtube.com/watch?v=SF7m08pgQJg&list=PLqnWYrfCqvm76wCt6E0JnCIP1fVgMlnC-&index=1

Kubernetes YML Generator with Usage for Deployment and Service:
https://github.com/TechPrimers/k8s-spring-boot-example
https://static.brandonpotter.com/kubernetes/DeploymentBuilder.html


https://github.com/matthewpalmer/awesome-kubernetes

kubernetes Doc: 
https://medium.com/google-cloud/kubernetes-101-pods-nodes-containers-and-clusters-c1509e409e16
https://sookocheff.com/post/kubernetes/understanding-kubernetes-networking-model/
https://medium.com/tag/kubernetes/archive
https://www.quora.com/What-is-minikube-kubectl-and-kubelet
https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0

Docker Doc:
https://medium.com/swlh/deploying-spring-boot-applications-15e14db25ff0
https://medium.com/@alokpabalkar/docker-simplified-3212a18cc823

Practice k8s,docker doc:
https://medium.com/free-code-camp/learn-kubernetes-in-under-3-hours-a-detailed-guide-to-orchestrating-containers-114ff420e882


