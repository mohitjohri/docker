---
sort: 1
---

# Comparing With Application

## Intention
 * Run a nginx web server application
 * Understand what is an image
 * Understand what is a container
 * Basic operations on a container
 * States of the container

## Experiment 1
 1. We can run a nginx web server application by the below command
```bash
docker run --name mynginx -p 8090:80 -d nginx
```
 1. Verify the application working by visiting [http://localhost:8090](http://localhost:8090)
 1. We should be seeing the nginx welcome page
 1. We have now run a docker container (also an nginx application) from the nginx image

## Experiment 2
 1. We can see all the containers running by the below command
```bash
docker ps
```
 1. We should be seeing an output similar to the image below
![docker ps output](/L01-E02-P01.png)
 1. This command lists all the running container
 1. From the image we can observe the following
   1. The container ID: This is generated by docker when the container is created
   1. The image name: This is the name of the image that was used to spin up the container
   1. The container name: The name of the container. This is passes as --name argument. If not passed, docker generates a randome name
   1. The status: The status of the container

## Experiment 3
 1. Till now we have run a container, and seen info about it. Now lets stop the container by the below command
```bash
docker stop mynginx
```
 1. Now we can verify that the container is stopped by running the below command
```bash
docker ps
```
![docker ps output](/L01-E03-P01.png)
 1. The output should be similar to the image below indicating there are no containers running.
 1. We can verify that the application is not running by visiting the page [http://localhost:8090](http://localhost:8090) in incognito mode
 
## Experiment 4
 1. We have stopped the container and as expected the command `docker ps` is not showing our container.
 1. Lets see the stopped containers with `docker ps` command with `-a` option
```bash
docker ps -a
```
 1. The command should produce an output as the below image indicating that the container is stopped
![docker ps -a output](/Lesson-01-Experiment-04-Picture-01.PNG)
 1. From the image we can observe the status of the container is exited
 
## Experiment 5
 1. We now have a stopped container. Lets start it with the below command
```bash
docker start mynginx
```
 1. As seen earlier, we can confirm the container is running by the below command
```bash
docker ps
```
 1. Verify the application working by visiting [http://localhost:8090](http://localhost:8090) in incognito mode
 
## Experiment 6
 1. As seen earlier, lets not stop the container. And remove it in the next step
```bash
docker stop mynginx
```
```bash
docker rm mynginx
```
 1. As seen earlier, we can verify there is no containers in the running or stopped state by the below command
```bash
docker ps -a`
```
 
## Experiment 7
 1. We have now seen how to run a container, stop it and remove it. We can also create a container without running it with the command below
```bash
docker create --name mynginx -p 8090:80 nginx
```
 1. As seen earlier, we can verify that the container is create but not running with the below command
```bash
docker ps -a`
```
 1. Verify the application is not running by visiting [http://localhost:8090](http://localhost:8090) in incognito mode
 
## Experiment 8
 1. We now have a container that is created but not running. We can run it with the below command
```bash
docker start mynginx
```
 1. As seen earlier, we can confirm the container is running by the below command
```bash
docker ps
```
 1. Verify the application working by visiting [http://localhost:8090](http://localhost:8090) in incognito mode

## Experiment 9
 1. Its also possible to restart the container with the below command
```bash
docker restart mynginx
```
 1. We can verify the restart by observing the status of command below
```bash
docker ps
```
 
## Experiment 10
 1. Apart from starting, stoping containers we can also pause the container with the below command.
```bash
docker pause mynginx
``` 
 1. We can observe that container is paused with the below command
```bash
docker ps -a
```
 1. At this point, docker stop and pause would look similar. We will look the difference between stop and pause in a later section.
 
## Experiment 11
 1. As expected we can resume or unpause a paused container by the below command
```bash
docker unpause mynginx
```

## Experiment 12
 1. Apart for stopping a container it's also possible to kill a container with the below command
```bash
docker kill mynginx
```
 1. At this point, docker stop and kill would look similar. We will look the difference between stop and pause in a later section.
 1. We have now completed all the experiments that are part of this lesson. Lets leave it in a clean state by removing the container with the command below
```bash
docker rm mynginx
```

## Summary
From the expreriments conducted till now we could get understand the below points
 * Container is something like a running application. Image is something like a binary that was used to spin up the application. (We will refine this view in the next lesson)
 * Image is used to create a container
 * The container can be different states such as defined in Engine [api v1.24](https://docs.docker.com/engine/api/v1.24/)
   * created
   * restarting
   * running
   * paused
   * exited
   * dead
 * We will look in to state transition in a latter lesson
 * docker run command is used to create a container and get it running
 * docker create command is used to create a container
 * docker start command is used to move a container to running state from created or exited state
 * docker pause command is used to pause a container
 * docker unpause command is used to move a container from paused state to running state
 * docker stop/kill command is used to move a container from running state to exited state
 * docker ps command to list all running containers
 * docker ps -a command to list all running containers

## Test your self
 * What is an image?
 * What is a container?
 * What is the difference between a image and container?
 * Run, Stop, Remove the Container
   * Run a container from nginx image
   * Verfiy access to default page
   * Stop the container
   * Remove the container
 * Create, Start, Pause, Unpause, Stop and Remove
   * Create a nginx container
   * Start the created container
   * Verfiy access to default page
   * Pause the container
   * Verify the default page is not accessible
   * Unpause the container
   * Verfiy access to default page
   * Stop the container
   * Verify the default page is not accessible
   * Remove the container
   * Verify the removal with `docker ps -a` command