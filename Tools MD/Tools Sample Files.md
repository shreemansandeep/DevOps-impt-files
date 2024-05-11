ansible playbook to install the nginx and should be running 
---
- hosts: your_target_servers
  become: true
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: start service nginx
      service:
        name: nginx
        state: started    
		
    - name: Stop Nginx service
      service:
        name: nginx
        state: stopped

    - name: Uninstall Nginx
      apt:
        name: nginx
        state: absent		
--------------------------------------------------------------------------------------
dockerfile to install nginx

FROM ubuntu 
MAINTAINER user@gmail.com 

RUN apt-get update 
RUN apt-get install -y nginx 
CMD [“echo”,”Image created”] 
-----------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------

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
---------------------------------------------------------
dockerfile to install tomcat

FROM ubuntu:latest
MAINTAINER hello@gritfy.com
RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install openjdk-8-jdk wget
RUN mkdir /usr/local/tomcat
RUN wget http://www-us.apache.org/dist/tomcat/tomcat-8/v8.5.16/bin/apache-tomcat-8.5.16.tar.gz -O /tmp/tomcat.tar.gz
RUN cd /tmp && tar xvfz tomcat.tar.gz
RUN cp -Rv /tmp/apache-tomcat-8.5.16/* /usr/local/tomcat/
EXPOSE 8080
CMD ["usr/local/opt/tomcat/bin/catalina.sh", "run"]
------------------------------------------------------------

k8s deployment.yml for nginx

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
----------------------------------------------------------------

k8s service.yml for nginx

apiVersion: v1
kind: Service
metadata:
 name: nginx-svc
 labels:
 app: nginx
spec:
 type: NodePort
 ports:
 - port: 80
 nodePort: 30080
 selector:
 app: nginx
-------------------------------
k8s pod.yml for nginx
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80
========================================================
	
Shell Script:

	Q1) How to backup database using shell script ?
	A: Create a new script file, for example "db_backup.sh", in a directory of your choice.
	Define variables for your database connection information, such as the host, port, username, and password.
	
			DB_HOST="your_host"
			DB_USER="your_username"
			DB_PASS="your_password"
			DB_NAME="your_db_name"

-> Use the "mysqldump"command to backup the database and save the output to a file.
mysqldump -h $DB_HOST -u $DB_USER -p$DB_PASS $DB_NAME > /path/to/backup/db_backup.sql

-> ompress the backup file using "gzip" or "tar" to reduce its size and save it in a folder of your choice
gzip /path/to/backup/db_backup.sql

-> You can add this script to a cron job to schedule regular backups.
0 3 * * * /path/to/script/db_backup.sh

Q2) How to do server provisioning using shell script ?
A:- Create a new script file, for example "server_provision.sh", in a directory of your choice.
     Define variables for the server's IP address, username, and password.
	 
	    SERVER_IP="your_server_ip"
		SERVER_USER="your_username"
		SERVER_PASS="your_password"
		
-> Use the ssh command to connect to the server and run commands to set up the server.

ssh $SERVER_USER@$SERVER_IP <<EOF
    # commands to install and configure software packages
    apt-get update
    apt-get install -y apache2
    service apache2 start
    # commands to set up user accounts and permissions
    useradd -m -d /home/newuser newuser
    echo newuser:newpassword | chpasswd
EOF
