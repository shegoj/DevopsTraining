#  Devops Essentials Module 1 [ March 2019]

## Working with Pipeline

We are diving a little deeper into Jenkins, showing how to use pipeline plugins to deploy and using Jenkinsfile too. 
Pipeline will be leveraging Ansible, AWS-CLI and Terraform for infrastructure and application builds

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


###  Create a new Job to create a file /tmp/withpipeline on the frontend node. use Pipeline instead of freestyle project,
- authenticate into Jenkins web application
- Create a new item (job), priovide a name .
- select pipeline
- add this code to the pipeline:
- ```
node {
  stage('Clean workspace') {
    deleteDir()
            
  }
  
  stage('Checkout source') {
    git url: 'htpps://yourrepo'
    sh " ./secondscript.sh 'withpipeline'"
  
  }
}```
- run the job



 

###  create a new job to use the script for deployment
- create a new Freestyle Jenkins job
- specify Source Code Managment  
- on the build box, specify [ sh -x myfirstscript.sh ]
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
- sh -x myfirstscript.sh "newdirectory"

 


### if all goes well, merge inprogess branch to master branch

- git checkout master
- git merge inprogress
- git push

### check to see the merge is successful and update deploy job accordingly.






