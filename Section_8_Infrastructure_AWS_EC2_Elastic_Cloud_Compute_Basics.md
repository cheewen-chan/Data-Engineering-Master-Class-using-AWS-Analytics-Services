## Managing EC2 Using AWS CLI
* Let us understand how we can manage EC2 Instances using AWS CLI.
* We should be able to take care of all the tasks related to managing EC2 Instances via AWS CLI. Here are some of the examples.
* Create Key Pair or use existing Key Pair.
* Create EC2 Instances
* Attach Security Groups to EC2 Instances
* Manage Security Group Rules
* Stop, Restart as well as Terminate EC2 Instance.
* Allocate and Attach Elastic IP.
* Describe an instance to get all the metadata associated with it.
* You can get help on aws ec2 by using the following command.

```
aws ec2 help
```

```
aws ec2 describe-instances \
 --profile itvadmin \
 --region us-west-1 > instances.json
```

Let us warm up by performing some basic tasks against EC2 Instances using AWS CLI. We will be using the itvadmin profile as the user account have Administrator Access on AWS Account.

* **Describe instances and get the instance ids.**

```
aws ec2 describe-instances \
 --region ap-south-1
```

```
aws ec2 describe-instances \
 --profile itvadmin \
 --region ap-south-1
```

```
aws ec2 describe-instances \
 --profile itvadmin \
 --region ap-south-1 | \
grep -i instanceid
 
```
* **You can use one of the instance ids and get instance status**
```
aws ec2 describe-instance-status \
--instance-id i-07c085b765f162233 \
 --profile itvadmin \
 --region ap-south-1
```
* **Stop the instance and validate whether the instance is stopped or not.**

```
aws ec2 stop-instances \
 --instance-id i-07c085b765f162233 \
 --profile itvadmin \
 --region ap-south-1
```

```
aws ec2 describe-instance-status \
 --instance-id i-07c085b765f162233 \
 --profile itvadmin \
 --region ap-south-1
```

* **Start the instance and validate whether the instance is started or not.**
```
aws ec2 start-instances \
 --instance-id i-07c085b765f162233 i-00f80143dc2e77b85 \
 --profile itvadmin \
 --region ap-south-1
```

```
aws ec2 describe-instance-status \
 --instance-id i-07c085b765f162233 i-00f80143dc2e77b85 \
 --profile itvadmin \
 --region ap-south-1
```

* **List Elastic IPs that are allocated so far.**
```
aws ec2 describe-addresses \
 --profile itvadmin \
 --region ap-south-1


```
