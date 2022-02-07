<h1>Documentation for installing an containerized Apache webserver and securing it</h1>
<br>

**Getting Started** <br>
Log into your Linode machine via SSH using the setps outlined in the virutalization lab documentation. Once you have established a connection, you can start installing the apache web server using docker with this documentation.

<br> **Pulling docker immage** <br>
Now you will pull the apache docker image we are using to install the container on your machine.

1. `docker run -d --name WebServerLab -e TZ=MST -p 80:80 ubuntu/apache2:2.4-20.04_beta `
2. Now open a browser on your local machine and connect to the URL: ip:8080 (Use the same IP as for SSH)

**Getting started with the container** <br>
First we need to remote into the container via bash from the existing SSH connection into the Linode and then you will install a small text editor in order to configure the server.

1. First figure out your container ID or name by typing `docker ps`
2. Use this to terminal into the container (replace "apache2-container" with either your container ID or name) `docker exec -it apache2-container /bin/bash`
3. Now update the container `apt-get update`
4. Now you can install the text editor `apt-get install nano`

**Configure the apache server**
In this part you will edit the security section of the apache configure file to make the whole server more secure.

1.
