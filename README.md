# Data Engineering Master Class using AWS Analytics Services

Notes of Udemy Course **https://www.udemy.com/course/data-engineering-using-aws-analytics-services/**

## Introduction to the Course

## Setup local environment
* Jupyter Lab using Docker
```

Here are the steps that are involved in setting up jupyter lab using Docker.

You can google for “Jupyter Lab using Docker”

Choose one of the images from the official website. I have chosen jupyter/minimal-notebook

You can run the below commands to start the container with JupyterLab.

docker create \
-p 9999:8888 \
--user root \
-e GRANT_SUDO=yes \
--name awsanalytics jupyter/minimal-notebook
 
docker start awsanalytics
 
# Use the below command to get the token so that you can login using Jupyter Lab environment.
docker logs awsanalytics
Now go to the browser and enter http://localhost:9999/lab and enter the token copied from logs to login.
```

* Understanding Jupyter Lab Environment
* Understanding Jupyter Lab Environment
* Install Python boto3
* Running Shell Commands
* Install AWS CLI

## Setup Environment for Practice Cloud 9
* Introduction to Cloud9
* Setup Cloud9
* Overview of Cloud9 IDE
* Docker and AWS CLI on Cloud9
* Cloud9 and EC2
* Accessing Web Applications
* Allocate and Assign Static IP
* Changing Permissions using IAM Policies
* Increasing Size of EBS Volume
* Opening ports for Cloud9 Instance
* Setup Jupyter lab on Cloud9 Instance
* Open SSH Port for Cloud9 EC2 Instance
* Connect to Cloud9 EC2 Instance using SSH
