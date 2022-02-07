<h1>Documentation for installing an containerized Apache webserver and hardening it</h1>
<br>

**Getting Started** <br>
Log into your Linode machine via SSH using the setps outlined in the virutalization lab documentation. Once you have established a connection, you can start installing the apache web server using docker with this documentation.

<br> **Pulling docker immage** <br>
Now you will pull the apache docker image we are using to install the container on your machine.

1. `docker run -d --name WebServerLab -e TZ=MST -p 80:80 ubuntu/apache2:2.4-20.04_beta `
2. Now open a browser on your local machine and connect to the URL: ip:8080 (Use the same IP as for SSH)

<h2>Securing the Apache Webserver<h/2>
<br>
  
**asd** <br>

1.
