<h3>Documentation for Installing a containerized Apache Webserver and Hardening it</h3>
<br>

**Getting Started:** <br>
1.	Log into your Linode machine via SSH using the steps outlined in the “Virtualization Lab” documentation. 
2.	Once you have established a connection, you can start installing the Apache web server using Docker by following this documentation.

**Pulling in the Docker Image:** <br>
1.	Pull the Apache based Docker image we are using to install the container onto your machine by typing: <br>
     		`docker run -d --name WebServerLab -e TZ=MST -p 80:80 ubuntu/apache2:2.4-20.04_beta`
2.	Now open a browser on your local machine and connect to the URL:  <br>
      		`http://[Your Linode Server’s IP]` <br>
	*Note: This should bring up the default Apache web page for your new server <br>*

**Getting Started with the Container:** <br>
-	We will remote into the container install a text editor so we can configure the server.
1.	First figure out your container ID or container name by typing: <br>
      		`docker ps` <br>
	*Note: If you used to command provided in the previous steps, the container name should be “WebServerLab”.*
2. 	Then, use this name to get into the container by typing: <br>
      		`docker exec -it [Your Apache Container’s Name] /bin/bash`
3.	Now, update the container by typing: <br>
      		`apt-get update && apt-get full-upgrade -y`
4.	Finally, you can install the text editor by typing: <br>
			`apt-get install nano -y`
5.	You need to ensure that SSH is installed by typing: <br>
			`apt install ssh -y`
6.	Then exit out of the docker container by typing: <br>
			`exit`

**Securing SSH:** <br>
Disabling Remote Root Access and Adding a new “dev” User:
-	In this section we will disable remote access to the root account of the server and set up proper accounts to be used with just the level of privilege required for each to operate.
1.	Back in the terminal, create a user account called “dev” for the development team to use by typing:  <br>	
      		`useradd –m –s /bin/bash dev`
2.	Now, create a safe and unique password for your new account by using this command to prompt a password change (after which you type in your new password): <br>
      		`passwd dev` <br>
      		`[Your New Password]`
3.	Add the "dev" user into the superusers group by typing: <br>
		`usermod -aG sudo dev`
5.	Now you can disable remote root account access by first editing the SSH configuration file by typing: <br>
      		`nano /etc/ssh/sshd_config`
4.	Once in the file, press the down arrow key until you find the line that says: “PermitRootLogin yes”. 
5.	Then, simply add a “#” symbol in front of the line (just like all the other lines). Once done, press ctrl+X, and then type Y and hit ENTER.
6.	Finally, type the command: <br>
      		`systemctl restart ssh`
7.	Then type "exit" and hit ENTER; Re-login with the “dev” user credentials you created, since the root account is now disabled on SSH.

**Setting up SSH Keys for the “dev” User:** <br>
-	This part will guide you through setting up private key authentication for the newly created “dev” account.
1.	Open a new PowerShell terminal on your machine as well as any other computer you want to have to access the Linode “dev” account.
2.	Now generate a private SSH key for your new “dev” account by typing: <br>
      		`ssh-keygen –t rsa` 
3.	Press ENTER when you are prompted to enter a save location. 
4.	Press ENTER twice when prompted for a new passphrase.
5.	On the Linode server machine, type the command: <br>
			`ssh keygen` 
6.	Press ENTER when you are prompted to enter a save location. 
7.	Press ENTER twice when prompted for a new passphrase.
8.	Then, go into the new directory by typing: <br>
			`cd .ssh`
9.	Create the “authorized_keys” file by typing: <br>
			`echo “” > authorized_keys`
10.	Now copy your public key to the server by typing: <br>
			`type \[Your User Profile’s Home Path]\.ssh\id_rsa.pub | ssh dev@[Your Linode IP Address] “cat >> .ssh/authorized_keys”`
 

**Disabling SSH Password Authentication:** <br>
-	Lastly, we will disable the password authentication method completely for SSH connections.
1.	Log back into your Linode using the “dev” account
2.	Switch to the root user by typing: <br>
      		`su root`
3.	Edit the SSH config file by typing:  <br>
      		`nano /etc/ssh/sshd_config`
4.	Use the down key until you find the line that says: “PasswordAuthentication yes”.
5.	Replace the “yes” with a “no” in that line.
6.	Press CTRL+X then type y and press ENTER
7.	Now restart the SSH system by typing: <br>
      		`systemctl restart ssh`
