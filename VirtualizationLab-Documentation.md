<h3>Documentation for Creating a Linode with Docker installed</h3>
<br>

**Getting Started** <br>
Login into your Linode account or create a new account if you don't have one.

1. On the left-hand side of the Linode main dashboard, make sure that “Linodes” is selected. 

2. Click the “Create” button in the center of the screen. 

<br> **Setting up** <br>
Now you will configure main settings of your Linode.

1. Under the “Choose a Distribution” section of the new page that popped up, select the “Ubuntu 20.4 LTS” option from the drop-down menu. 



2. Select “Region” and select your desired region from the drop-down menu.  

3. Chose the “Linode Plan” and select “Dedicated CPU” and chose the “Dedicated 4 GB” option.  

4. Select “Linode Label” and type in your desired label. 

5. Select “Root Password” and create a newly created secure password.

<br> **SSH Key/Access** <br>
To be able access and install Docker after you configured the server, you need to pre set your SSH key. If you don't have an SSH key already, look up an SSH keygen tutorial and return here once you have one.

1. Import your SSH key into Linode by selecting “Add an SSH Key” and then putting in the desired label and your public key. 

2. Now you can select “Create Linode” on the right-hand side of the screen and start your Linode. 

<br> **SSH Access** <br>
Now you will establishe an SSH connection to your newly created Linode once its up and showing the green running light on the dashboard of your Linode.

1. Open a terminal application of your choice that is cappable of SSH.

2. Return to your created Linode dashboard and click the copy button on the top left of the site, next to SSH Access: `ssh root@0.0.0.0`

3. Back on your terminal paste the copied SSH command in and enter `yes` when prompted.

<br> **Installing Docker** <br>
It should now say root@ip or root@localhost in the terminal. Lastly you can update and install docker on your Linode. Type in the following commands.

1. `apt update && apt upgrade –y`

2. `reboot`

3. Wait a few minutes or until your Linode dashboard shows the server fully rebooted and then repeat SSH Access steps 2 and 3 to reconnected to your Linode.

4. `apt install docker –y` 

5. `apt install docker.io -y` 

 
