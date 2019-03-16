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

###  Install git on your Toolbox machine

- sudo yum install git -y
- type git to check that it is working

###  synch Jenkins user with your Github repo using ssh keys

- ensure you are jenkins [user]  su - jenkins
- authenticate to your Github  repo https://github.com 
- go to https://github.com/settings/keys , then hit "New SSH Key"
- Give it a title. In the key section, copy  content of /var/lib/jenkins/.ssh/id_rsa.pub into the section
- go to https://github.com/settings/keys , then hit "New SSH Key"


###  Create a new Git project 
- Paste  https://github.com/new on your browser to create a new Github Repository. Call it devops101
 

###  push your first update to your new repo
- ensure you are jenkins [user]. cd to /tmp
- echo "# devops101 first commit updated by [[your name ]] " >> README.md
- git init
- git add README.md
- git commit -m "first commit"
- git remote add origin git@github.com:shegoj/devops101.git
- git push -u origin master
- Refresh the Github page. The ReadMe file should be here 


###  push your second update to your new repo
- edit the ReadMe file . Append "Another line added" to the file
- git commit -a -m "file update"
- git push
- Verify the file is update on Github


###  Update web server home page
- check the web server is up and running 
- create a job to push an index file [ index.html]  to /var/www/html on the frontend node . ou can put "Hello this is [[your name]]  in the file.
- restart httpd
- check that the home page is now updated



