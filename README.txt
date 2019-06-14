1. INSTALLING ORACLE VM VIRTUALBOX

-RUN VIRTUAL BOX SETUP AND INSTALL IT.

2. CREATE VIRTUAL MACHINE AND INSTALLING UBUNTU 16.04 VERSION ON VIRTUALBOX

- OPEN THE VIRTUALBOX
- Click 'New' button to open a dialog.
-Type a name for the new virtual machine. Since I am planning to install Ubuntu 16.04, I'll enter 'ubuntu1604'. 
-The memory size depends on your host machine memory size.
-Accept the default 'Create a virtual hard drive now' and click 'Create' button.
-Continue to accept the default 'VDI' drive file type and click 'Next' button.
-Change the storage type from the default 'Dynamically allocated' to 'Fixed size' to increase performance.
-For the virtual hard drive space, the default value is 8GB which is too little for RNA-Seq analysis. 
-Click 'Create' button and VirtualBox will generate Ubuntu virtual machine.
-Now the virtual machine is created. We are ready to install Ubuntu in this virtual machine.
-Select your new virtual machine and click 'Settings' button. Click on 'Storage' category and then 'Empty' under Controller:IDE.
-Click "CD/DVD" icon on right hand side and select the ubuntu ISO file to mount.
-When downloading Ubuntu ISO file, make sure to selecte 64-bit version.
-Back to Oracle VM VirtualBox Manager, click on the new Ubuntu virtual machine and hit 'Start' button. 
- Now you shall see a 'Welcome' screen. Click 'Install Ubuntu' button.
-Note that the installation process may differ a little bit from version to version.

3.INSTALLING HYPERLEDGER COMPOSER

-The following are prerequisites for installing the required development tools:

-Operating Systems: Ubuntu Linux 14.04 / 16.04 LTS (both 64-bit), or Mac OS 10.12
-Docker Engine: Version 17.03 or higher
-Docker-Compose: Version 1.8 or higher
-Node: 8.9 or higher (note version 9 and higher is not supported)
-npm: v5.x
-git: 2.9.x or higher
-Python: 2.7.x
-A code editor of your choice, we recommend VSCode.
**If installing Hyperledger Composer using Linux, be aware of the following advice:

-Login as a normal user, rather than root.
-Do not su to root.
-When installing prerequisites, use curl, then unzip using sudo.
-Run prereqs-ubuntu.sh as a normal user. It may prompt for root password as some of it's actions are required to be run as root.
-Do not use npm with sudo or su to root to use it.
-Avoid installing node globally as root.**

4. INSTALLING ALL PREREQUISITES IN UBUNTU.

- curl -O https://hyperledger.github.io/composer/latest/prereqs-ubuntu.sh

- chmod u+x prereqs-ubuntu.sh

- ./prereqs-ubuntu.sh

-Congratulations, the installation of the pre-requisites for Hyperledger Composer is complete! 

5. INSTALLING THE DEVELOPMENT ENVIRONMENT.

-Step 1: Install the CLI tools
-Step 2: Install Playground
-Step 3: Set up your IDE
-Install VSCode from this URL: https://code.visualstudio.com/download
-Step 4: Install Hyperledger Fabric
- mkdir ~/fabric-dev-servers && cd ~/fabric-dev-servers

- curl -O https://raw.githubusercontent.com/hyperledger/composer-tools/master/packages/fabric-dev-servers/fabric-dev-servers.tar.gz
tar -xvf fabric-dev-servers.tar.gz 

- cd ~/fabric-dev-servers
- export FABRIC_VERSION=hlfv12
- ./downloadFabric.sh
-Congratulations, you've now installed everything required for the typical Developer Environment.

6.Starting and stopping Hyperledger Fabric

-~/fabric-dev-servers/startFabric.sh
-~/fabric-dev-servers/stopFabric.sh

7.Start the web app ("Playground")

-    composer-playground
- It will typically open your browser automatically, at the following address: http://localhost:8080/login
- You should see the PeerAdmin@hlfv1 Card you created with the createPeerAdminCard script on your "My Business Networks" screen in the web app
- if you don't see this, you may not have correctly started up your runtime!

-Congratulations, you've got all the components running, and you also know how to stop and tear them down when you're done with your dev session.

8. NOW YOU WILL USE THE DEVELOPMENT ENVIRONMENT TO CREATE NEW ADMIN CARD AND YOU WILL STORE THE DATA ON THEM.

- ./startFabric.sh
- 

composer network install --card PeerAdmin@hlfv1 --archiveFile dist/project1.bna


- composer network reset -c PeerAdmin@hlfv1 -v 0.0.8


- composer network start -c PeerAdmin@hlfv1 -n project1 -V 0.0.2 -A admin -S adminpw


- composer card import -f admin@project1.card -c admin@project1
- 

composer network ping -c admin@project1


-composer-rest-server

9. ALTERNATE WAY TO DIRECTLY RUN REST SERVER AT PARTICULAR PORT
- 

#PORT=3005 composer-rest-server -c admin@project1 -n always -u true -d n

10. NOW YOUR SERVER BACKEND WILL BE READY AND U CAN OPEN THE FTML FILES PLACED IN HTM FILES FOLDER

-There is upload data .html named file which can be used to store data on the hyperledger fabric server Blockchain.
-AS MAIN PAGE .html named file is placed over there which can help you to verify the marksheet in two option that is wethet the full degree details or the another one that is highest degree only.

11 Finished.



