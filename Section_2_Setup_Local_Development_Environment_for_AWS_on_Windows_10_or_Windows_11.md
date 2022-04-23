# Setup Local Development Environment for AWS on Windows 10 or Windows 11

## Section 2 WSL Windows Setup
* Open Windows Powershell
* Install Ubuntu Distribution
```
PS C:\Users\Lenovo> wsl --list --all
Windows Subsystem for Linux Distributions:
Ubuntu (Default)
PS C:\Users\Lenovo>
```
* **List Active Machine**

```
PS C:\Users\Lenovo> wsl --list
Windows Subsystem for Linux has no installed distributions.
Distributions can be installed by visiting the Microsoft Store:
https://aka.ms/wslstore
PS C:\Users\Lenovo> wsl -l -v
  NAME      STATE           VERSION
* Ubuntu    Running         1
PS C:\Users\Lenovo>
```

* **Connect to wsl from powershell**
```
PS C:\Users\Lenovo> wsl
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

rishi@mylocalpc:/mnt/c/Users/Lenovo$
rishi@mylocalpc:/mnt/c/Users/Lenovo$ ls
'3D Objects'
 AWS_BOTO_Project
 AndroidStudioProjects
 AppData
...........
ntuser.ini
 package-lock.json
 source
rishi@mylocalpc:/mnt/c/Users/Lenovo$
```

```
PS C:\Users\Lenovo> wsl -d Ubuntu
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

rishi@mylocalpc:/mnt/c/Users/Lenovo$

```

* **Password reset for wsl**
```
PS C:\Users\Lenovo> wsl -u root
Welcome to Ubuntu 20.04.2 LTS (GNU/Linux 4.4.0-18362-Microsoft x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Thu Apr 21 17:27:28 IST 2022

  System load:    0.52      Processes:              9
  Usage of /home: unknown   Users logged in:        0
  Memory usage:   75%       IPv4 address for eth2:  169.254.99.115
  Swap usage:     2%        IPv4 address for wifi0: 192.168.1.7

1 update can be installed immediately.
0 of these updates are security updates.
To see these additional updates run: apt list --upgradable


The list of available updates is more than a week old.
To check for new updates run: sudo apt update


This message is shown once a day. To disable it please create the
/root/.hushlogin file.
root@mylocalpc:/mnt/c/Users/Lenovo# passwd rishi
New password:
Retype new password:
passwd: password updated successfully
root@mylocalpc:/mnt/c/Users/Lenovo# exit
logout
PS C:\Users\Lenovo> wsl
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

rishi@mylocalpc:/mnt/c/Users/Lenovo$ sudo echo hi
[sudo] password for rishi:
hi
rishi@mylocalpc:/mnt/c/Users/Lenovo$ sudo apt-get install python
```


## **Setup Python venv and pip on Ubuntu**
```
# install python
rishi@mylocalpc:/mnt/c/Users/Lenovo$ sudo apt-get install python3-venv pip
Reading package lists... 
Done ...........
# Update list if unable to find packages  
sudo apt update
rishi@mylocalpc:/mnt/c/Users/Lenovo$ sudo apt update
[sudo] password for rishi:

```
* **Validate venv setup**
```
rishi@mylocalpc:/home$ sudo python3.8 -m venv demo-venv
rishi@mylocalpc:/home$ ls demo-venv/
bin  include  lib  lib64  pyvenv.cfg  share
```

* **install configparser**
```

rishi@mylocalpc:/home$ pip install configparser
Collecting configparser
  Downloading configparser-5.2.0-py3-none-any.whl (19 kB)
Installing collected packages: configparser
Successfully installed configparser-5.2.0
rishi@mylocalpc:/home$

```
## Setup AWS CLI on Windows and Ubuntu using Pip
```
pip install awscli
# logout and login to wsl
```

## Create AWS IAM User and Download Credentials
* Create aws user 
* Give programatic access
* Assign to Admin Permission group 
* Download access keys csv file
  * Sample File Below
```
User name,Password,Access key ID,Secret access key,Console login link
user1,,ACCESS KEY,SECRET ACCESS KEY,https://118454160685.signin.aws.amazon.com/console
```

## Configure AWS CLI on Windows
```
rishi@mylocalpc:~$ aws s3 ls
Unable to locate credentials. You can configure credentials by running "aws configure".
rishi@mylocalpc:~$ aws configure
AWS Access Key ID [None]: < ACCESS KEY ID >
AWS Secret Access Key [None]: < SECRET KEY >
Default region name [None]:
Default output format [None]:
rishi@mylocalpc:~$ aws s3 ls
2022-02-15 14:22:59 mytrainingcourses
rishi@mylocalpc:~$
```
## Create Python Virtual Environment for AWS Projects
```
rishi@mylocalpc:/mnt/c/Users/Lenovo$ mkdir -p /Projects/Internal/bootcamp/data-engineering-on-aws
rishi@mylocalpc:~$ cd /Projects/Internal/bootcamp/data-engineering-on-aws
# Make Virtual Environment
rishi@mylocalpc:~$ sudo python3.8 -m venv demo-venv
rishi@mylocalpc:~$ ls -ltra demo-venv/
total 0
drwxr-xr-x 1 rishi rishi 512 Apr 22 12:01 ..
drwxr-xr-x 1 root  root  512 Apr 22 12:01 include
drwxr-xr-x 1 root  root  512 Apr 22 12:01 lib
lrwxrwxrwx 1 root  root    3 Apr 22 12:01 lib64 -> lib
-rw-r--r-- 1 root  root   70 Apr 22 12:01 pyvenv.cfg
drwxr-xr-x 1 root  root  512 Apr 22 12:01 share
drwxr-xr-x 1 root  root  512 Apr 22 12:01 .
drwxr-xr-x 1 root  root  512 Apr 22 12:01 bin
rishi@mylocalpc:~$
rishi@mylocalpc:~$ 
# Activate Virtual Environment
rishi@mylocalpc:~$ source de-venv/bin/activate
(de-venv) rishi@mylocalpc:~$

```
## Setup Boto3 as part of Python Virtual Environment
```
rishi@mylocalpc:~$ source de-venv/bin/activate
(de-venv) rishi@mylocalpc:~$ pip install boto3
Collecting boto3
  Downloading boto3-1.21.45-py3-none-any.whl (132 kB)
     |████████████████████████████████| 132 kB 4.9 MB/s
Collecting jmespath<2.0.0,>=0.7.1
  Using cached jmespath-1.0.0-py3-none-any.whl (23 kB)
Collecting botocore<1.25.0,>=1.24.45
  Downloading botocore-1.24.45-py3-none-any.whl (8.7 MB)
     |████████████████████████████████| 8.7 MB 7.5 MB/s
Collecting s3transfer<0.6.0,>=0.5.0
  Using cached s3transfer-0.5.2-py3-none-any.whl (79 kB)
Collecting urllib3<1.27,>=1.25.4
  Downloading urllib3-1.26.9-py2.py3-none-any.whl (138 kB)
     |████████████████████████████████| 138 kB 10.3 MB/s
Collecting python-dateutil<3.0.0,>=2.1
  Using cached python_dateutil-2.8.2-py2.py3-none-any.whl (247 kB)
Collecting six>=1.5
  Downloading six-1.16.0-py2.py3-none-any.whl (11 kB)
Installing collected packages: jmespath, urllib3, six, python-dateutil, botocore, s3transfer, boto3
Successfully installed boto3-1.21.45 botocore-1.24.45 jmespath-1.0.0 python-dateutil-2.8.2 s3transfer-0.5.2 six-1.16.0 urllib3-1.26.9
(de-venv) rishi@mylocalpc:~$

(de-venv) rishi@mylocalpc:~$ python
Python 3.8.10 (default, Mar 15 2022, 12:22:08)
[GCC 9.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import boto3
>>> s3_client = boto3.client('s3')
>>> s3_client.list_buckets()
{'ResponseMetadata': {'RequestId': '9WQT15TNH7DWZMRP', 'HostId': 'IO84Ao0lWZGBuHHqhXrObi/pdPonxvvx1/KIXJSJ8NP6fMeD5hctOaokEk2M7Il6CepBL5kwnbQ=', 'HTTPStatusCode': 200, 'HTTPHeaders': {'x-amz-id-2': 'IO84Ao0lWZGBuHHqhXrObi/pdPonxvvx1/KIXJSJ8NP6fMeD5hctOaokEk2M7Il6CepBL5kwnbQ=', 'x-amz-request-id': '9WQT15TNH7DWZMRP', 'date': 'Fri, 22 Apr 2022 06:49:24 GMT', 'content-type': 'application/xml', 'transfer-encoding': 'chunked', 'server': 'AmazonS3'}, 'RetryAttempts': 0}, 'Buckets': [{'Name': 'mega.nz', 'CreationDate': datetime.datetime(2022, 2, 15, 8, 50, 33, tzinfo=tzutc())}, {'Name': 'mytradingcourses', 'CreationDate': datetime.datetime(2022, 2, 15, 8, 52, 59, tzinfo=tzutc())}], 'Owner': {'DisplayName': 'ris.arora', 'ID': '2fedc5e5b66770f2381ece35fd51398c644f15e62bc50837c9178161cd6fa9c8'}}
>>>
```

## Setup Jupyter Lab and Validate boto3
```
(de-venv) rishi@mylocalpc:~$ pip install jupyterlab
Collecting jupyterlab
  Downloading jupyterlab-3.3.4-py3-none-any.whl (8.7 MB)
     |████████████████████████████████| 8.7 MB 346 kB/s

Installing collected packages: prometheus-client, ....., jupyterlab
Successfully installed MarkupSafe-2.1.1 ..... zipp-3.8.0
(de-venv) rishi@mylocalpc:~$
(de-venv) rishi@mylocalpc:~$ pip install jupyterlab
^CERROR: Operation cancelled by user
(de-venv) rishi@mylocalpc:~$ jupyter lab
[I 2022-04-22 12:31:51.359 ServerApp] jupyterlab | extension was successfully linked.
...
[I 2022-04-22 12:31:54.366 ServerApp] Jupyter Server 1.16.0 is running at:
[I 2022-04-22 12:31:54.367 ServerApp] http://localhost:8889/lab?token=42b012231384f2cffc09383077b61031de1d7fa0222bd54c
[I 2022-04-22 12:31:54.368 ServerApp]  or http://127.0.0.1:8889/lab?token=42b012231384f2cffc09383077b61031de1d7fa0222bd54c
[I 2022-04-22 12:31:54.368 ServerApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 2022-04-22 12:31:54.422 ServerApp]

    To access the server, open this file in a browser:
        file:///home/rishi/.local/share/jupyter/runtime/jpserver-7016-open.html
    Or copy and paste one of these URLs:
        http://localhost:8889/lab?token=42b012231384f2cffc09383077b61031de1d7fa0222bd54c
     or http://127.0.0.1:8889/lab?token=42b012231384f2cffc09383077b61031de1d7fa0222bd54c

```


* **Validating Jupyter notebook connecting with AWS**
```
import boto3
s3_client = boto3.client('s3')

buckets = s3_client.list_buckets()['Buckets']
buckets
            [{'Name': 'mega.nz',
            'CreationDate': datetime.datetime(2022, 2, 15, 8, 50, 33, tzinfo=tzutc())},
            {'Name': 'mytradingcourses',
            'CreationDate': datetime.datetime(2022, 2, 15, 8, 52, 59, tzinfo=tzutc())}]


buckets_name = buckets[1]['Name']
buckets_name
            'mytradingcourses'


bucket = buckets[0]
bucket
            {'Name': 'mega.nz',
            'CreationDate': datetime.datetime(2022, 2, 15, 8, 50, 33, tzinfo=tzutc())}


buckets_names = [bucket['Name'] for bucket in buckets]

buckets_names
            ['mega.nz', 'mytradingcourses']

```
