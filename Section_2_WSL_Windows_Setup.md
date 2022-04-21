# Section 2 WSL Windows Setup
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

rishi@Atishree:/mnt/c/Users/Lenovo$
rishi@Atishree:/mnt/c/Users/Lenovo$ ls
'3D Objects'
 AWS_BOTO_Project
 AndroidStudioProjects
 AppData
...........
ntuser.ini
 package-lock.json
 source
rishi@Atishree:/mnt/c/Users/Lenovo$
```
