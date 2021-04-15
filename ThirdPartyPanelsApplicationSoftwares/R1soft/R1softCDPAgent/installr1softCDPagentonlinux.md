---
title: How to install r1soft CDP agent on Linux server
description: 
published: true
date: 2021-04-15T20:08:40.468Z
tags: 
editor: markdown
dateCreated: 2021-04-15T20:08:40.468Z
---

Download CDP agent from

https://dist.r1soft.com/download/

I has 32 and 64 bit windows and linux agents. So download the correct version

Once downloaded, extract .zip file

The archive extracted contains two folders: one with .deb packages ("deb-linux64 / deb-linux32") and one with .rpm packages ("rpm-linux64 / rpm-linux32").

If you are installing on Debian or Ubuntu, choose the folder with .deb packages.

If you are installing on Redhat or CentOS, choose the folder with .rpm packages.

Each folder contains a set of the Backup Agent components:

- serverbackup-setup
- serverbackup-agent
- serverbackup-enterprise-agent
- serverbackup-async-agent-2-6

 **Installation command on CentOS / Redhat**

Use the cd command to go to the folder rpm-linux64 / rpm-linux32  with the packages  and then run the following command

```
rpm -Uvh *
```

**Installation command on Ubuntu / Debian**

Use the cd command to go to the folder deb-linux64 / deb-linux32  with the packages  and then run the following command:

```
dpkg -i *.deb
```

and it will install cdp agent

after that run

```
service cdp-agent restart
```

Add server key

```
r1soft-setup --get-key https://72.18.207.240
```

**kernel headers installation**

R1soft some time ask to install kernel header if he do not find the kernel compatible to run

while installing kernel package using the command

```
/usr/bin/r1soft-setup --get-module
```

if you came across the  below errors :  


> Unable to find a valid source directory.
> Please install the kernel headers for 
> your operating system.
{.is-danger}


Then don't panic  this can simply be resolved by running the below commands

**For CentOS**

```
root@server[#] yum install kernel-devel kernel-headers
```

 If you are running PAE kernel

```
root@server[#] yum install kernel-PAE-devel
```

 If you are running xen kernels

```
root@server[#]yum install kernel-xen-devel
```

If you are running one of the beta kernels then,

```
add --enablerepo=cloudlinux-updates-testing
```

at the end of yum command, like this:

```
yum install kernel-devel --enablerepo=cloudlinux-updates-testing
```

Now, just re-execute the command :

```
/usr/bin/r1soft-setup --get-module

```

**For Debian / Ubuntu**

Error Message

```
sh-3.1# r1soft-setup --get-module
Checking if module needs updated
Checking for binary module
Waiting / 
No binary module found
Gathering kernel information
Gathering kernel information complete.
Creating kernel headers package
Checking '/lib/modules/2.6.18-4-686/source/' for kernel headers
Checking '/usr/src/kernels/2.6.18-4-686-i686/' for kernel headers
Checking '/lib/modules/2.6.18-4-686/build/' for kernel headers
Unable to find a valid source directory.
Please install the kernel headers for your operating system.
```

**Do the following steps:**

Make sure you have updated version

```
# apt-get update
```

Install linux-header package under Debian or Ubuntu Linux
Type the following apt-get command:

```
# apt-get install linux-headers-$(uname -r)

```

**Sample Output**

```
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
 linux-headers-2.6.18-4 linux-kbuild-2.6.18
The following NEW packages will be installed:
 linux-headers-2.6.18-4 linux-headers-2.6.18-4-686 linux-kbuild-2.6.18
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 3607kB of archives.
After unpacking 20.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
 linux-headers-2.6.18-4 linux-headers-2.6.18-4-686
Install these packages without verification [y/N]? y
Get:1 http://archive.debian.org etch/updates/main linux-headers-2.6.18-4 2.6.18.dfsg.1-12etch2 [3163kB]
Get:2 http://archive.debian.org etch/main linux-kbuild-2.6.18 2.6.18-1 [168kB]
Get:3 http://archive.debian.org etch/updates/main linux-headers-2.6.18-4-686 2.6.18.dfsg.1-12etch2 [276kB]
Fetched 3607kB in 4s (729kB/s) 
Selecting previously deselected package linux-headers-2.6.18-4.
(Reading database ... 42105 files and directories currently installed.)
Unpacking linux-headers-2.6.18-4 (from .../linux-headers-2.6.18-4_2.6.18.dfsg.1-12etch2_i386.deb) ...
Selecting previously deselected package linux-kbuild-2.6.18.
Unpacking linux-kbuild-2.6.18 (from .../linux-kbuild-2.6.18_2.6.18-1_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.18-4-686.
Unpacking linux-headers-2.6.18-4-686 (from .../linux-headers-2.6.18-4-686_2.6.18.dfsg.1-12etch2_i386.deb) ...
Setting up linux-headers-2.6.18-4 (2.6.18.dfsg.1-12etch2) ...
Setting up linux-kbuild-2.6.18 (2.6.18-1) ...
Setting up linux-headers-2.6.18-4-686 (2.6.18.dfsg.1-12etch2) 
```

Now, just re-execute the command :

```
# /usr/bin/r1soft-setup --get-module
```

Sample Output

```
Checking if module needs updated
Checking for binary module
Waiting                       /          
No binary module found
Gathering kernel information
Gathering kernel information complete.
Creating kernel headers package
Checking '/lib/modules/2.6.18-4-686/source/' for kernel headers
Checking '/usr/src/kernels/2.6.18-4-686-i686/' for kernel headers
Checking '/lib/modules/2.6.18-4-686/build/' for kernel headers
Found headers in '/lib/modules/2.6.18-4-686/build/'
Compressing...
uploading kernel package                                                                                                                                      99% 3549KB   3.5MB/s   00:00 ETA
Starting module build...
Complete.                                
Saving kernel module to '/lib/modules/r1soft/hcpdriver-cki-2.6.18-4-686.ko'
Kernel module is now installed.
Use '/etc/init.d/cdp-agent restart' to load the new driver
```

Then restart the cdp agent

```
# /etc/init.d/cdp-agent restart
```



