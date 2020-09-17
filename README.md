# node-red 
## important : this build will not run without an SD card addtional memory, due to Node-Red storage requeriments -Minimum 2GB Memory stick for AXC F 2152 (Part# 1043501 or 1061701)

## Part 1 - Installation of Balena Engine   https://github.com/PLCnext/Docker_GettingStarted 
This is part of a series of articles that demonstrate how to install Balena-engine on PLCnext controller and work with OCI containers.
In this article, we will install the Balena-engine and start OCI containers.

### Installation 

### Establish the Connections 
1.	Connect the AXC F 2152 controller to Internet-Provider and Linux OS via LAN-cable.
2.	Start the terminal on Linux OS and establish the SSH-Connection to PLC via command line "ssh admin@192.168.1.10".
3.	Change to root via "su -" (root password have to be setup https://github.com/plcnextusa/PLCnext-Guides/blob/master/Appendices/Appendix%204%20How%20to%20create%20a%20root%20user%20in%20SSH.pdf)
4.	Make sure your Internet connection is intact, via command-line ping 8.8.8.8


### Download the Project to the controller 

```bash
root@axcf2152:~# git clone https://github.com/PLCnext/Docker_GettingStarted.git 

root@axcf2152:~# cd Docker_GettingStarted
```
### Install Balena 

To install balena-engine run the setup.sh
```bash
root@axcf2152:~# chmod -c 777 setup.sh
root@axcf2152:~# ./setup.sh
root@axcf2152:~# /etc/init.d/balena start
```

## Part 2 - Installation of node-red container 

### Install node-red from the official node-red container hub https://hub.docker.com/r/nodered/node-red 

```bash
root@axcf2152:~# balena-engine run -it --restart unless-stopped -p 1880:1880 --network=host --privileged --name=mynodered nodered/node-red
```
```bash
root@axcf2152:~# update-rc.d -f firewall remove
root@axcf2152:~# reboot
```
This command will install and create your container which will run with the balena-engine from boot by default, and if your unit is connected to the internet so should be Node-Red, allowing to install any contribution you desire from the interface

Also you can start and stop your Node_red container anytime by using the following commands.
```bash
root@axcf2152:~# balena-engine start mynodered
root@axcf2152:~# balena-engine stop mynodered
```


Enjoy it!
