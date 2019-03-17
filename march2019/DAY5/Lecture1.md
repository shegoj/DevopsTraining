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
```code
node {
  stage('Clean workspace') {
    deleteDir()
            
  }
  
  stage('Checkout source') {
    git url: 'https://yourrepo'
    sh "chmod +x secondscript.sh"
    sh " ./secondscript.sh 'withpipeline'"
  }
} ``` 
- run the job


###  create a Jenkins paramter which takes a file name to be created. Update the job to use the parameter for file creation. Use this to create file /tmp/created_via_paramter
- edit the job. select "This project is parameterised". add a "string type"  paramter. Call it "filename". Give it a default value "nofile"
- update script as below. Adapt it for your repository ans script name.
```code
node {
  stage('Clean workspace') {
    deleteDir()
            
  }
  
  stage('Checkout source') {
    git url: 'https://github.com/shegoj/DevopsTraining.git'
  }
  
  stage ('execute script') {
   
    sh "secondscript.sh  ${params.filename}"
  }
}
```
- run build




