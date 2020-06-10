## INTRO TO DOCKER
Terminology:
- **Image** is the blueprint for building, template
- **Container** is the running copy of the template
> Analogy: image is the cookie recipe, container is the cookie (u/Xendrak:reddit)

We will go over:
- pulling docker images
- running docker containers
- building with dockerfiles
- running home-made docker image


### 1. Install Docker:
 - [Windows install](https://docs.docker.com/docker-for-windows/install/)
- [Ubuntu Install](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04)
- [Mac install](https://docs.docker.com/docker-for-mac/install/)

> Verify install with the ```docker``` command in terminal. You should see available commandsflast

### 2. Run your first Docker container
```docker run hello-world```
> the docker image in pulled from docker hub and it is built and run

### 3. Build your own container
```docker pull alpine```
 > check containers on system 
 ```docker image ls``` lists images on system

 - the container exists on local system, but is not running.

 to run

 ```docker run --name sample-docker -it alpine```
 > the 'it' flag is for "interactive terminal"
 > you are now in a running docker container
 **CONGRADULATIONS**

 To leave

 ```exit```

No changes to system persist

> it is possible to save system changes with the ```docker commit```
command 
> Example:
- make a new dir and file in a running docker image
- exit docker image
- use ```docker ps -a``` command to see running images  
- ```docker commit [CONTAINTER ID] [new_image_name]``` will make a new image with the saved changes

> *THIS IS NOT THE PREFERED METHOD TO SET CONTAINER. IT IS RECOMMENDED TO USE DOCKERFILES* 

### 4. DOCKERFILES and the fun begins

1. clone this repository into your docker-enabled system
2. ```cd``` into directory where dockerfile resides
> [dockerfile explained](https://docs.docker.com/engine/reference/builder/)
3. ```docker build -t flask-sample:latest .```
- builds the docker image from the docker file.
- -t flag is to tag image (useful for versioning)
- DONT FORGET THE **'.'** at the end (I often miss this)

4. You see the docker layers being built.

You should see 

``` Successfully built ########```

``` Successfully tagged flask-sample:latest```

5. Now the home-made docker image is ready to run.

RUN

```docker run -d -p 5000:5000 flask-sample ```

- -d flag is detached, does not run in same terminal 
- -p flag sets ports for docker and host machine


> now if you go to https://localhost:5000 you should see the running flask app

**YOU CAN MAKE CHANGES IN THE DOCKERFILE and FLASK APP, when you rebuild it will only make changes to layers that need changes**


> Docker github has some great resources to learn more 

> [DOCKER LABS](https://github.com/docker/labs/blob/master/beginner/chapters/alpine.md)