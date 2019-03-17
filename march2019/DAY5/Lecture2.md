#  Devops Essentials Module 1 [ March 2019]

## Working AWS-CLI


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


###  Use AWS-CLI to list running EC2 in your environments.
- 
- ensure aws-cli is configured appropriately
- ```run aws ec2 describe-instances --filters   "Name=instance-state-name,Values=running"   |  jq -r ".Reservations[] | .Instances[] | .InstanceId"```

###  Use AWS-CLI to list running EC2 Frontent node. Display its IP address, instance id and tags
- 
- ensure aws-cli is configured appropriately
- aws ec2 describe-instances --filters "Name=tag:Name,Values=Frontent"   "Name=instance-state-name,Values=running"   |  jq -r ".Reservations[] | .Instances[] | [.InstanceId, .PrivateIpAddress, .Tags[].Value]"


###  Exercise: Your boss wants you to create a job to export all the runing ec2 instances to a csv file. The file should contain IP and instance name.
- 


