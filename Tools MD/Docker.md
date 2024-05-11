Docker : containerization tool.

virtulization :

vmware : multiple operating systems manage --->> windows , ubuntu , linux..

Hypervisor --->>> vmware.--->> virtualization.

heavy weight --->> hard ware (cpu , memory , hard disk utilization)

not easy to move.

effective utilization hardware resourcess.


===========================================================


continerzation :

docker install -->>> dokerdaemon --->>> containers

container is nothint but operating system.-

container is nothing but server.

leight weight --->>>no need to take hardware utilization 

easy to move.

less utilization of hardware resources..


=========================================================

Docker : developers develope the code and that code can be shipped them into container..

application -->>> end user.

one ec2 instance ---->> docker install -->>> containers --->>> n no.of conatinaers it dependent on the system hardware..

n no .of apps -->> deploy..

=======================================================================

Docker key components :

docker image --->> pull

docker conainer : image -->>> container

dockerhub  / docker registry : images -->> backup 

Docker file -->> image create.

Docker architecture:

Docker is a client / server architecture.


Docker work flow    : Dev / QA / UAt / PROD
===================================================




docker installation steps:

1. we need to take one ec2 instance..

2. install docker 

yum install -y docker

service docker start


ifconfig -a

docker 0 --->>> bridge network.

c1 , c2 , c3 .....IP allocate. ( internal) --->> throgh loop back address.

=============================================================================
Docker Image Basic commands :

1.docker pull nginx  =====>> Pull docker image to local host

2. docker images  ===>> Show all images on the host

3.docker rmi 39c2d1c93266  ===>> Remove a specific image

4. sudo docker run -itd -p 30:80 ubuntu

5. docker rmi -f $(docker images)  ==>> Remove all images forcibly.

=============================================================================

Docker Container Basic commands :

1.docker run -itd -p 2000:80 nginx ===>> creating docker container 

2.docker ps (show running containers)

3.docker ps -a (show running and exited containers)

4.docker stop 725a4a748b3b

5. docker start 725a4a748b3b

6. docker restart 725a4a748b3b

7. docker ps -aq (return all container ids)

8. docker rm 725a4a748b3b

9.docker logs 725a4a748b3b  ==>>> Check container logs

10. Getting into the container  ==>> docker exec -it 725a4a748b3b /bin/bash

11. docker rm -f $(docker ps -aq)  ==>>> Remove all containers forcibly.


============================================================================

Docker file: it is atext file .

it contains instructions --->>> docker/ conatiner instructions.

keywords

from copy environment port..

Dockerfile -->> name should be unique.

Creating Docker Image

1. To create docker image we need to write Dockerfile

2. To write Dockerfile we should know the instructions.

Dockerfile Instructions 

1. As per convention filename is Dockerfile  and This file is usually present is project root directory


FROM ==>> FROM is used to specify the base image.

LABEL ==>>This is to add labels, labels are like meta info for the images

RUN : Run commands on docker image

WORKDIR : It makes the directory as PWD if the folder is not present it creates.

EXPOSE : This is to open a port on the container

CMD :This is useful to run commands at Docker run time. and This command can be used for starting applications at container start time.

ENTRYPOINT :This is similar to CMD, it is also runtime instruction but it has little different behaviour.

COPY : To copy file from local host to docker image and Source can be only local filesystem

ADD :ADD a file to docker image and Source can be local filesystem or remote url
-------------------------------------------------------------------------------------------------------------
Q. write a docker file for installing java and tomacat and copy war file

# Use the official Java 11 image as the base image
FROM openjdk:11-jdk-slim

# Set the environment variables for Tomcat
ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH

# Install Tomcat
RUN apt-get update && apt-get install -y wget && \
    wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.54/bin/apache-tomcat-9.0.54.tar.gz && \
    tar -zxvf apache-tomcat-9.0.54.tar.gz && \
    rm apache-tomcat-9.0.54.tar.gz && \
    mv apache-tomcat-9.0.54 $CATALINA_HOME

# Copy the war file into the container
COPY myapp.war $CATALINA_HOME/webapps/

# Set the working directory to the Tomcat installation directory
WORKDIR $CATALINA_HOME

# Expose the default Tomcat port
EXPOSE 8080

# Start Tomcat when the container launches
CMD ["catalina.sh", "run"]

==============================================================
# docker file for nodejs application

# Base image
FROM node:16-alpine

# Set the working directory
WORKDIR /app

# Copy the application code
COPY . .

# Install application dependencies
RUN npm install

# Build the application
RUN npm run build

# Expose a port
EXPOSE 3000

# Set the command to run when the container starts
CMD ["npm", "start"]
==============================================================

jenkins integrate with docker.

step 1:  we need to install this plugin : PublishoverSSH.

step 2: we need to configure SSH between jenkins and docker instancess.

step 3:  jenkins dash board ==>> manage jenkins ==>> configure system ===>> add ssh servers ==>>> docker3 user credentials 

step 4 : jenkins ==>> create job.


docker3     ALL=(ALL)           NOPASSWD: ALL


===============================================================================================

docker volume create myvol1

docker run -itd -p 8002:80 --name vasuapp -v myvol1:/myapp alpine

docker network ls

sudo docker run -itd --name sriniapp1 -v /home/docker3/sekhar/:myapp1 alpine

sudo docker inspect bridge
   
  docker network create --driver bridge javahome
  
  sudo docker run -itd --name sriniapp3 --network javahome  alpine
  sudo docker ps
  sudo docker network ls
  docker inspect 8d5eeaeed9db
  sudo docker ps
  docker inspect 088e6edaaf9e
  sudo docker ps
  sudo docker run -itd --name sriniapp4 --network javahome  alpine
  docker inspect network
  docker inspect javahome
  docker exec -it 8d5eeaeed9db1
  docker exec -it 8d5eeaeed9db1 ash
  ping sriniapp4
  ping 172.18.0.3
  ping sriniapp4
  ping sriniapp3
 
 Only stopped containers can be listed using: docker ps --filter "status=exited" or docker ps -f "status=exited"

sudo usermod -aG docker jenkins

chmod 777 /var/run/docker.sock


"CMD" is used to define the default command that will be run when the container is started. This can be overridden by the user when they run the container, using the docker run command.
"ENTRYPOINT" is used to define the command that will always be run when the container is started. This cannot be overridden by the user.
