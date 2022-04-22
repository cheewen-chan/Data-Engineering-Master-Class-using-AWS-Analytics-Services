## Setup Environment for Practice Cloud 9
* Introduction to Cloud9
* Setup Cloud9
![image](https://user-images.githubusercontent.com/4485129/162073604-d9bb5d8e-ccd9-44dd-a472-5b53ff7252d1.png)

### **Validate in IDE below are installed**
  * git
  * java  
  * docker
  * python
```
c9ideUser:~/environment $ git version
git version 2.32.0
c9ideUser:~/environment $ 


c9ideUser:~/environment $ docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
c9ideUser:~/environment $ 


c9ideUser:~/environment $ java -version
openjdk version "11.0.14.1" 2022-02-08 LTS
OpenJDK Runtime Environment Corretto-11.0.14.10.1 (build 11.0.14.1+10-LTS)
OpenJDK 64-Bit Server VM Corretto-11.0.14.10.1 (build 11.0.14.1+10-LTS, mixed mode)
c9ideUser:~/environment $ javac -version
javac 11.0.14.1
c9ideUser:~/environment $ 


c9ideUser:~/environment $ python
python                    python2.7                 python2-config            python3.7                 python3.7m                python3.7m-x86_64-config  python-config             
python2                   python2.7-config          python3                   python3.7-config          python3.7m-config         python3-config            
c9ideUser:~/environment $ 
c9ideUser:~/environment $ python3.7 
Python 3.7.10 (default, Jun  3 2021, 00:02:01) 
[GCC 7.3.1 20180712 (Red Hat 7.3.1-13)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()
c9ideUser:~/environment $ 
```
* **Get Service List** 
```
c9ideUser:~/environment $ sudo systemctl status <SERVICE NAME>
```

### Docker and AWS CLI on Cloud9

### Cloud9 and EC2
### Accessing Web Applications
```
c9ideUser:~/environment $ sudo systemctl status httpd
c9ideUser:~/environment $ sudo systemctl start httpd
c9ideUser:~/environment $ sudo systemctl status httpd                                                                                                                                                                              
● httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; disabled; vendor preset: disabled)
  Drop-In: /usr/lib/systemd/system/httpd.service.d
           └─php-fpm.conf
   Active: active (running) since Fri 2022-04-22 12:47:02 UTC; 2s ago
     Docs: man:httpd.service(8)
 Main PID: 12559 (httpd)
   Status: "Processing requests..."
    Tasks: 47
   Memory: 13.6M
   CGroup: /system.slice/httpd.service
           ├─12559 /usr/sbin/httpd -DFOREGROUND
           ├─12619 /usr/sbin/httpd -DFOREGROUND
           ├─12621 /usr/sbin/httpd -DFOREGROUND
           ├─12622 /usr/sbin/httpd -DFOREGROUND
           ├─12623 /usr/sbin/httpd -DFOREGROUND
           └─12624 /usr/sbin/httpd -DFOREGROUND

Apr 22 12:47:02 ip-172-31-37-64.ec2.internal systemd[1]: Starting The Apache HTTP Server...
Apr 22 12:47:02 ip-172-31-37-64.ec2.internal systemd[1]: Started The Apache HTTP Server.

```
* **Telnet Setup**
```
c9ideUser:~/environment $ sudo yum install telnet -y
c9ideUser:~/environment $ telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
^]
HTTP/1.1 400 Bad Request
Date: Fri, 22 Apr 2022 12:48:35 GMT
Server: Apache/2.4.52 ()
Content-Length: 226
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>400 Bad Request</title>
</head><body>
<h1>Bad Request</h1>
<p>Your browser sent a request that this server could not understand.<br />
</p>
</body></html>
Connection closed by foreign host.
c9ideUser:~/environment $ 
```

### Allocate and Assign Static IP
### Changing Permissions using IAM Policies
### Increasing Size of EBS Volume
### Opening ports for Cloud9 Instance
### Setup Jupyter lab on Cloud9 Instance
### Open SSH Port for Cloud9 EC2 Instance
### Connect to Cloud9 EC2 Instance using SSH
