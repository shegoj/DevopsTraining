#  Devops Essentials Mdodule 1 [ March 2019]

## Lecture 1 [ VM Creation and Access ]

This guide provides simple practical steps to learning and using Linux. It will take about an hour to complete

---

## 

You will try out different Linux commands to  solve real life problems as a way of familiarising yourself with the environment.

---

## Intended Audience

Users who undertand basic concept of the computer system.

---

## Requirements

Ensure the following is installed and working

- putty https://www.dropbox.com/sh/cho8pwn3tlfz37o/AADcF15c1vXwVhu4LE23BkVIa?dl=0 
- set it up as directed by the instructor

**DO NOT PROCEED UNTIL THESE ARE PRESENT**

---

## Getting started

---

###  You have been asked to ensure password authentication to the Frontend node is possible. 

- connect to Frontend node. and sudo to root. [ sudo -i ]
- create frontend user if it doesn't exist .  [ useradd frontend-user -m ]
- create a pasword for the user [ passwd  frontend-user ]

###  Now from Backend node, try to authenticate to Frontend node. 

- connect to Backend node.
- From there, try to connect to the frontend node using frontend-user/frontend-user.  [ ssh fronent-user@ip-for-node ] # This might fail because password authentication is disabled

###  Enable Password authentication on Frontend node. 
- sudo -i.
-  [ vi /etc/ssh/sshd_config ] .. change [PasswordAuthentication no]   to [ PasswordAuthentication yes ]
-  restart sshd  [ service sshd restart ] 
- Try exercise 2 again




###  Now repeat the process for Backend node with (user) backend-user and password (backend-user).



#### You have been asked to create a new node where  Jenkins  will be deployed 
     Provision the node as normal. Label it as ToolServer. Ensure port 8080 and 22 inbound are open

#### Install Jenkins on the new node  
- connect to the node
- sudo -i
- yum update -y
- yum install -y java-1.8.0-openjdk.x86_64 -y    [ this is to install Java ]
- wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo 
- rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
- yum install jenkins -y 
- service jenkins start
- check that jenkins is running : use http://publicip:8080



#### Generate SSH keys for Jenkins.   
- connect to the node
- sudo -i
- vi /etc/passwd.  Edit file to make jenkins user a login account look for a line that begins with jenkins . Change the last entry on the line from "/bin/false" "/bin/bash"
- Add Jenkins to sudo users  :  vi /etc/sudoers.d/90-cloud-init-users     [jenkins ALL=(ALL) NOPASSWD:ALL ]
- ssh-keygen
     
      

#### Copy the key to Frontend node
- ssh-copy-id frontend-user@oip-frontend-node


#### Create a  Jenkins job( pipeline) to create file /tmp/helloworld on Frontend node
- Add Jenkins to sudo users  :  vi /etc/sudoers.d/90-cloud-init-users     [jenkins ALL=(ALL) NOPASSWD:ALL ]
- ssh-keygen   


#### Create a  Jenkins job( pipeline) to create file /tmp/helloworld on Backend node. 
      su frontend-user -   you may  use this code [ ssh frontend-user@ip -v  -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null 'touch /tmp/helloworld'


##### Exercise: Use Jenkins to deploy HTTPD (Apache) to the Frontend node. you may need to remove existing one if its already deployed

 
#### Excercise: Use Jenkins to deploy MariaDB to the Backend-node

