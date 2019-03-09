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

- Make sure you can login and have access to shared Linux server and https://www.tutorialspoint.com/unix_terminal_online.php

---

###  Task 1: The Department has been asked to setup infrastructure to support a new product launch.  The product will have a frontend and a backend system. We need a test bed to to try out a few initial confoguration work. Setup two small machines to achieve this .  The following requirements must be met
- Use Amazon Linux 2 AMI/ T2 Micro
- Machine should accessible over the Internet ONLY via ssh
- Security Group for each machine should be named correctly
- Label the machines as: [ Machine A ->  NAME: Frontend, TYPE: Micro || Machine B ->  NAME: Backend, TYPE: Micro ]
- Use the same key to access the machines and keep the key safe
- Test and ensure you are able to access the nodes [ ssh to the nodes ]
- Create a user called frontend-user on node 1 with a password.
- From Node 2, attempt to connect to node 1 with the new user using a passwd  **
- Go back to Node 1. Switch to front-end user, then generate a private and public key for  the user **




#### Create a user called frontend-user on node 1 with a password . Generate a private and public key for the user
     `sudo -i ` to become root user
      useradd frontend-user -m
      passwd  frontend-user

#### Attempt to connect from node 2 to node 1 with the new user using a passwd 
      from node 2
      ssh frontend@node1-IP. This will fail . We wil revist this later to fix 
   
#### Go back to Node 1. Switch to front-end user, then generate a private and public key for  the user
      su frontend-user -  
      ssh-keygen     

