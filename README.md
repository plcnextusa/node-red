# node-red 


## Part 1 - Installation of Balena Engine ##
This is part of a series of articles that demonstrate how to install Balena-engine on PLCnext controller and work with OCI containers.
In this article, we will install the Balena-engine and start OCI containers.

### Installation ###

### Establish the Connections ###
1.	Connect the AXC F 2152 controller to Internet-Provider and Linux OS via LAN-cable.
2.	Start the terminal on Linux OS and establisch the SSH-Connection to PLC via commandline "ssh admin@192.168.1.10".
3.	Change to root via "su -" (root password have to be setup LINK)
4.	Make sure your Internet connection is intact, via command-line ping 8.8.8.8.

### Download the Project to the controller ###

[ root@axcf2152:/opt/plcnext/# git clone https://github.com/PLCnext/Docker_GettingStarted.git

root@axcf2152:/opt/plcnext/# cd Docker_GettingStarted
### Install Balena ###

To install balena-engine run the setup.sh

root@axcf2152:~# chmod +x setup.sh
root@axcf2152:~# ./setup.sh


# Part 2 - Installation of node-red container #

### Install node-red from the official node-red container hub( https://hub.docker.com/r/nodered/node-red ) ###

root@axcf2152:~# balena-engine run -it -p 1880:1880 --network=host --privileged --name=mynodered nodered/node-red


This command will install and create your container which will run with the balena-engine from boot by default, and if your unit is connected to the internet so should be Node-Red, allowing to install any contribution you desire from the interface. 

