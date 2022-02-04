<h3>Documentation for installing an containerized Apache webserver and hardening it</h3>
<br>

**Getting Started** <br>
Log into your Linode machine via SSH using the setps outlined in the virutalization lab documentation. Once you have established a connection, you can start installing the apache web server using docker with this documentation.

<br> **Pulling docker immage** <br>
Now you will pull the apache docker image we are using to install the container on your machine.

1. `docker pull ubuntu/apache2`
2. `docker run -d --name apache2-container -e TZ=UTC -p 8080:80 ubuntu/apache2:2.4-21.10_beta`
3. Now open a browser on your local machine and connect to the URL: ip:8080 (Use the same IP as for SSH)
