# Infrastructure - AWS EC2 Advanced

In this section we will continue with AWS EC2 to understand how we can manage EC2 instances using AWS Commands and also how to install additional OS modules leveraging bootstrap scripts.

* Getting Started with AWS EC2
* Understanding AWS EC2 Metadata
* Querying on AWS EC2 Metadata
* Fitering on AWS EC2 Metadata
* Using Bootstrapping Scripts with AWS EC2 Instances to install additional softwares on AWS EC2 instances
* Create an AWS AMI using AWS EC2 Instances
* Validate AWS AMI - Lab

## Bootstrapping 
* Using Bootstrapping Scripts with AWS EC2 Instances to install additional softwares on AWS EC2 instances

Using Bootstrapping Scripts we  Launch EC2 instance using Ubuntu 18.04 and install below softwares automatically on server creation
* Install Apache Web Server
* Install Python3 Pip
* Install AWS CLI using pip

We add the bwlow script in bootstrap section to prepare the ec2 instance as it is launched.
```
#!/bin/bash
apt update -y
apt install apache2 -y
apt install python3-pip -y
python3 -m pip install awscli
```

## Create an AMI
The EC2 instance is myec2-DE and we will name the image as myec2-DE_AMI.
* Go to EC2 Dashboard and then to Instances.
* Select the instance for which you want to create AMI.
* Go to Storage and click on the Volume.
* Create Snapshot for the Volume selected.
* Go to Actions and click on Create Image

## Creating AMI image from CLI
```
aws ec2 create-image \
  --instance-id i-ID \
  --name webAppAMI \
  --description "A sample AMI with pre installed apache web server"
```

* **Sample Run**
```
rishi@mylocalpc:~$ aws ec2 describe-instances | grep -i instanceid
                    "InstanceId": "i-0ccf2182410eb42d8",
rishi@mylocalpc:~$ 

rishi@mylocalpc:~$ aws ec2 create-image \
                    --instance-id "i-0ccf2182410eb42d8" \
                    --name my-DE-AMI \
                    --description "my First APi Image"
{
    "ImageId": "ami-0dc22b673db40ca05"
}
rishi@mylocalpc:~$

```

## Create an AWS AMI using AWS EC2 Instances

Create instance using aws cli

```
aws ec2 run-instances \
  --image-id ami-013f17f36f8b1fefb \
  --count 1 \
  --instance-type t2.micro \
  --key-name keyname \
  --security-group-ids sg-ID \
  --user-data file://ec2_user_data.sh
```
