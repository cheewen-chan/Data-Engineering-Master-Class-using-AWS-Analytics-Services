## Setup Environment for Practice Cloud 9
* Introduction to Cloud9
* Setup Cloud9
![image](https://user-images.githubusercontent.com/4485129/162073604-d9bb5d8e-ccd9-44dd-a472-5b53ff7252d1.png)

* **Validate in IDE below are installed**
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
c9ideUser:~/environment $ python3.7 version
python3.7: can't open file 'version': [Errno 2] No such file or directory
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
