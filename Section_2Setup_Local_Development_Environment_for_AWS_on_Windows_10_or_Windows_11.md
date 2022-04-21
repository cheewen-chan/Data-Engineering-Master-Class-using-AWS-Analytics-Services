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
rishi@Atishree:/mnt/c/Users/Lenovo$ sudo apt-get install python3-venv
Reading package lists... Done
...........
# Update list if unable to find packages  
sudo apt update
rishi@Atishree:/mnt/c/Users/Lenovo$ sudo apt update
[sudo] password for rishi:

```


## Setup AWS CLI on Windows and Ubuntu using Pip

```

```
## Create AWS IAM User and Download Credentials
## Configure AWS CLI on Windows
## Create Python Virtual Environment for AWS Projects
## Setup Boto3 as part of Python Virtual Environment
## Setup Jupyter Lab and Validate boto3
