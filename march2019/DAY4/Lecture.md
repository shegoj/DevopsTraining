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


###  create a script for the file creation task, and add the script to your git repo 
- log on to the Toolserver box as jenkins user 
- create a new directory /tmp/wkspace. mkdir /tmp/wkspace
- cd /tmp/wkspace
- git clone git@://yourRepoUrl
- cd dev* 
- echo "ssh frontend-user@ip -v  -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null 'touch /tmp/helloworld2'" >> myfirstscript.sh
- git add myfirstscript.sh 
- git commit -m "Added a deployment script"
- git push

 

###  create a new job to use the script for deployment
- create a new Freestyle Jenkins job
- specify Source Code Managment  
- on the build box, specify [ sh -x /devop101/myfirstscript.sh ]
- run build


###  change the content of myfirstscript.sh content in your repo to create different files... /tmp/helloworld3, /tmp/helloworld4 etc
- use previous steps	


###  Add a new functionality to the  script which should allow passing parameter to the script. The change should be commited in a separate branch. Call the branch "inprogress"

- cd /tmp/wkspace
- cd dev* 
- git pull  
- git checkout -b inprogress  
- now update the script. Replace content with this new line:   ssh frontend-user@ip -v  -o StrictHostKeyChecking=no -o UserKnownHostsFile=/dev/null "touch /tmp/$1"
- git commit -am "updated run script"  
- git push -u origin inprogress  


### Create a new job to run/test the branch


### if all goes well, merge inprogess branch to master branch

- git merge inprogress
- git checkout master
- git push

### check to see the merge is successful and update deploy job accordingly.






