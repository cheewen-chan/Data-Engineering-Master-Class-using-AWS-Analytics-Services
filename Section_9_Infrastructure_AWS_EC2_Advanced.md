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
  --image-id ami-0dc22b673db40ca05 \
  --count 2 \
  --instance-type t2.micro \
  --key-name DE-AWS \
  --security-group-ids sg-ID \
  --user-data file://ec2_user_data.sh
```

* **SampleRun**
```
rishi@mylocalpc:~$ cat bootstrap.sh
#!/bin/bash
apt update -y
apt install apache2 -y
apt install python3-pip -y
python3 -m pip install awscli
rishi@mylocalpc:~$ aws ec2 run-instances \
>   --image-id ami-0dc22b673db40ca05 \
>   --count 2 \
>   --instance-type t2.micro \
>   --key-name DE-AWS \
>   --user-data ec2_user_data.sh

rishi@mylocalpc:~$ aws ec2 run-instances   --image-id ami-0dc22b673db40ca05   --count 2   --instance-type t2.micro   --key-name DE-AWS   --user-data ec2_user_data.sh
{
    "Groups": [],
    "Instances": [
        {
            "AmiLaunchIndex": 0,
            "ImageId": "ami-0dc22b673db40ca05",
            "InstanceId": "i-080b4ebb059b71c66",
            "InstanceType": "t2.micro",
            "KeyName": "DE-AWS",
            "LaunchTime": "2022-04-23T08:55:23.000Z",
            "Monitoring": {
                "State": "disabled"
            },
            "Placement": {
                "AvailabilityZone": "us-east-1b",
                "GroupName": "",
                "Tenancy": "default"
            },
            "PrivateDnsName": "ip-172-31-2-226.ec2.internal",
            "PrivateIpAddress": "172.31.2.226",
            "ProductCodes": [],
            "PublicDnsName": "",
            "State": {
                "Code": 0,
                "Name": "pending"
            },
            "StateTransitionReason": "",
            "SubnetId": "subnet-0d16aa20871111f4e",
            "VpcId": "vpc-066119b989a2011c2",
            "Architecture": "x86_64",
            "BlockDeviceMappings": [],
            "ClientToken": "3ad5fbf6-1bf5-497f-892e-4f07fe07a2dd",
            "EbsOptimized": false,
            "EnaSupport": true,
            "Hypervisor": "xen",
            "NetworkInterfaces": [
                {
                    "Attachment": {
                        "AttachTime": "2022-04-23T08:55:23.000Z",
                        "AttachmentId": "eni-attach-0d7b846ffa9a63c5f",
                        "DeleteOnTermination": true,
                        "DeviceIndex": 0,
                        "Status": "attaching",
                        "NetworkCardIndex": 0
                    },
                    "Description": "",
                    "Groups": [
                        {
                            "GroupName": "default",
                            "GroupId": "sg-013750fe616f6597b"
                        }
                    ],
                    "Ipv6Addresses": [],
                    "MacAddress": "02:70:93:64:c3:23",
                    "NetworkInterfaceId": "eni-0761c5782fe9aed90",
                    "OwnerId": "118454160685",
                    "PrivateDnsName": "ip-172-31-2-226.ec2.internal",
                    "PrivateIpAddress": "172.31.2.226",
                    "PrivateIpAddresses": [
                        {
                            "Primary": true,
                            "PrivateDnsName": "ip-172-31-2-226.ec2.internal",
                            "PrivateIpAddress": "172.31.2.226"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Status": "in-use",
                    "SubnetId": "subnet-0d16aa20871111f4e",
                    "VpcId": "vpc-066119b989a2011c2",
                    "InterfaceType": "interface"
                }
            ],
            "RootDeviceName": "/dev/xvda",
            "RootDeviceType": "ebs",
            "SecurityGroups": [
                {
                    "GroupName": "default",
                    "GroupId": "sg-013750fe616f6597b"
                }
            ],
            "SourceDestCheck": true,
            "StateReason": {
                "Code": "pending",
                "Message": "pending"
            },
            "VirtualizationType": "hvm",
            "CpuOptions": {
                "CoreCount": 1,
                "ThreadsPerCore": 1
            },
            "CapacityReservationSpecification": {
                "CapacityReservationPreference": "open"
            },
            "MetadataOptions": {
                "State": "pending",
                "HttpTokens": "optional",
                "HttpPutResponseHopLimit": 1,
                "HttpEndpoint": "enabled",
                "HttpProtocolIpv6": "disabled",
                "InstanceMetadataTags": "disabled"
            },
            "EnclaveOptions": {
                "Enabled": false
            },
            "PrivateDnsNameOptions": {
                "HostnameType": "ip-name",
                "EnableResourceNameDnsARecord": false,
                "EnableResourceNameDnsAAAARecord": false
            },
            "MaintenanceOptions": {
                "AutoRecovery": "default"
            }
        },
        {
            "AmiLaunchIndex": 1,
            "ImageId": "ami-0dc22b673db40ca05",
            "InstanceId": "i-0177dc35ea8c54b2a",
            "InstanceType": "t2.micro",
            "KeyName": "DE-AWS",
            "LaunchTime": "2022-04-23T08:55:23.000Z",
            "Monitoring": {
                "State": "disabled"
            },
            "Placement": {
                "AvailabilityZone": "us-east-1b",
                "GroupName": "",
                "Tenancy": "default"
            },
            "PrivateDnsName": "ip-172-31-5-103.ec2.internal",
            "PrivateIpAddress": "172.31.5.103",
            "ProductCodes": [],
            "PublicDnsName": "",
            "State": {
                "Code": 0,
                "Name": "pending"
            },
            "StateTransitionReason": "",
            "SubnetId": "subnet-0d16aa20871111f4e",
            "VpcId": "vpc-066119b989a2011c2",
            "Architecture": "x86_64",
            "BlockDeviceMappings": [],
            "ClientToken": "3ad5fbf6-1bf5-497f-892e-4f07fe07a2dd",
            "EbsOptimized": false,
            "EnaSupport": true,
            "Hypervisor": "xen",
            "NetworkInterfaces": [
                {
                    "Attachment": {
                        "AttachTime": "2022-04-23T08:55:23.000Z",
                        "AttachmentId": "eni-attach-03e7d8af7d20eb419",
                        "DeleteOnTermination": true,
                        "DeviceIndex": 0,
                        "Status": "attaching",
                        "NetworkCardIndex": 0
                    },
                    "Description": "",
                    "Groups": [
                        {
                            "GroupName": "default",
                            "GroupId": "sg-013750fe616f6597b"
                        }
                    ],
                    "Ipv6Addresses": [],
                    "MacAddress": "02:1f:c0:0a:55:17",
                    "NetworkInterfaceId": "eni-03cc0ed39fff6c59d",
                    "OwnerId": "118454160685",
                    "PrivateDnsName": "ip-172-31-5-103.ec2.internal",
                    "PrivateIpAddress": "172.31.5.103",
                    "PrivateIpAddresses": [
                        {
                            "Primary": true,
                            "PrivateDnsName": "ip-172-31-5-103.ec2.internal",
                            "PrivateIpAddress": "172.31.5.103"
                        }
                    ],
                    "SourceDestCheck": true,
                    "Status": "in-use",
                    "SubnetId": "subnet-0d16aa20871111f4e",
                    "VpcId": "vpc-066119b989a2011c2",
                    "InterfaceType": "interface"
                }
            ],
            "RootDeviceName": "/dev/xvda",
            "RootDeviceType": "ebs",
            "SecurityGroups": [
                {
                    "GroupName": "default",
                    "GroupId": "sg-013750fe616f6597b"
                }
            ],
            "SourceDestCheck": true,
            "StateReason": {
                "Code": "pending",
                "Message": "pending"
            },
            "VirtualizationType": "hvm",
            "CpuOptions": {
                "CoreCount": 1,
                "ThreadsPerCore": 1
            },
            "CapacityReservationSpecification": {
                "CapacityReservationPreference": "open"
            },
            "MetadataOptions": {
                "State": "pending",
                "HttpTokens": "optional",
                "HttpPutResponseHopLimit": 1,
                "HttpEndpoint": "enabled",
                "HttpProtocolIpv6": "disabled",
                "InstanceMetadataTags": "disabled"
            },
            "EnclaveOptions": {
                "Enabled": false
            },
            "PrivateDnsNameOptions": {
                "HostnameType": "ip-name",
                "EnableResourceNameDnsARecord": false,
                "EnableResourceNameDnsAAAARecord": false
            },
            "MaintenanceOptions": {
                "AutoRecovery": "default"
            }
        }
    ],
    "OwnerId": "118454160685",
    "ReservationId": "r-07dbe00843ac205ee"
}
rishi@mylocalpc:~$ aws ec2 describe-instances | grep -i instanceid

                    "InstanceId": "i-0ccf2182410eb42d8",
                    "InstanceId": "i-080b4ebb059b71c66",
                    "InstanceId": "i-0177dc35ea8c54b2a",
rishi@mylocalpc:~$
rishi@mylocalpc:~$
```
