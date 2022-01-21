---
title:  Linux cPanel Server Hardening 
description: 
published: true
date: 2022-01-21T14:17:45.023Z
tags: 
editor: markdown
dateCreated: 2022-01-21T14:17:45.023Z
---



How a Linux cPanel/WHM machine can be hardened for security.

 

Warning:
Before making any modifications in configuration file please take a bakup of the same with the
format filename.conf-backup-dated-dd-mm-yy in the same location of the configuration file.
Step-by-step guide

1. Disable direct root login
Note: Please do not log out from your System after disabling the direct root login.

Please follow the steps until you create a dedicated SSH user and then you can log out. Otherwise you won’t be able to login to your system again.

Please be careful. Root user is the one that have the license to do anything in your system.

What if someone got access to the root user account?! Let’s disable direct root login by following the below steps.


Edit the SSH main configuration file.
vi /etc/ssh/sshd_config
You can find the below line.
#PermitRootLogin yes
Change it as below.
PermitRootLogin no
Restart SSH to update the changes.
/etc/init.d/sshd restart


That’s it!! You have disabled direct root login. Now follow the below steps to create a dedicated SSH user.


2. Create dedicated SSH user
After disabling the direct root login, the next step is to create a dedicated SSH user. (Only this user will have SSH login permission in your system) .


We are going to create a dedicated user called “sshusr” Please follow the below steps.
Create the user account.


useradd sshusr
Set Password.
passwd sshusr


Add this user to “/etc/sudoers” file. Simply edit this file or run the below command.
visudo
You can find a line as shown below.
root ALL=(ALL) ALL
The above line means root user can run any commands anywhere. Add the line given below under this line.
sshusr ALL=(ALL) ALL
Now save the file.
Now on, the user “sshusr” have the permission to run any commands anywhere. But for this you
have to add “sudo” the begining of every command that you execute as user “sshusr”.


For example, if you login as “sshusr” and want to restart Apache, you have to do it as shown below.
sudo /etc/init.d/httpd restart
You can also switch this user to root user. Please run the below command.
sudo su -
That’s it! :)
Now we have disabled direct root login and created a user called “sshusr” with full permission in your system.

But this doesn’t mean “sshusr” is a dedicated SSH user. May be there are other users in your system that have SSH shell access.

Please follow the below steps to block all those users and to set “sshusr” as dedicated SSH user.


Edit the mail SSH configuration file.
vi /etc/ssh/sshd_config
Add the below lines.
AllowUsers sshusr
Save the file and restart SSH service to update these changes.
/etc/init.d/sshd restart
That’s it!! You have created a dedicated SSH user. 


3. Change SSH default port


Everyone knows 22 is the default SSH port. So it’s always good to change this default port and set it to something un guessable. Please follow the below steps.


Here I’m going to change the port to 4242. Edit the main SSH configuration file.
vi /etc/ssh/sshd_config
You can find the below line.
#Port 22
Change it as below.
Port 4242
Restart SSH to update the changes.
/etc/init.d/sshd restart
That’s it!! You have changed the SSH port to 4242. :)
To login as “sshusr” from a remote Linux machine you can run the below command.
ssh sshusr@IP/Hostname -p 4242


4. Disable ping request

echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all


5.Disable Apache header information.


First, log in to your Linux server or VPS via shell (SSH) with root privileges. 2. Locate your
httpd.conf file, the main configuration file for Apache, sometimes called apache2.conf. Add the
following lines to the bottom of the file:

ServerTokens ProductOnly
ServerSignature Off

6.Hide PHP Version information
https://documentation.cpanel.net/display/CKB/How+to+Edit+Your+php.ini+File


disable_functions = phpinfo, eval, show_source, system, shell_exec, passthru, exec, popen,
proc_open, allow_url_fopen, symlink


7.Disable FTP. Use SFTP instead.
FTP is always the favourite back-door of hacker and there are a million ways to hack an FTP
account.


May be you are not that familiar with SSH and disabling FTP may put you in trouble. I have an
alternative option. If you are someone that wants the simplicity of FTP with the security features of SSH, you
can use SFTP. It is not a big deal. Any users that have SSH access to your system can use SFTP.
WinSCP is a SFTP client for Windows and you can find it here >> http://winscp.net/eng/index.php


8.Disable shell access for unknown users.
Onyly these users have shell access MySQL,ROOT,SSHUSR
grep bin/bash$ /etc/passwd
root:x:0:0:root:/root:/bin/bash
mysql:x:498:498:MySQL server:/var/lib/mysql:/bin/bash
sshusr:x:32012:32012::/home/sshusr:/bin/bash


9.Host.conf Hardening –Prevents IP spoofing and dns poisoning
Logrotate Enabled
Files from /usr/local/cpanel/logs selected below will be rotated based upon their size. The rotated
files will be compressed and stored in /usr/local/cpanel/logs/archive/. The files are named to include
the month in which they are rotated. Consequently, the file names do not relate in any way to the
content of the file being rotated. Files are only rotated when they grow larger than the WHM >>
Tweak Settings >> Log Rotation Size Threshold or the default of 300MB. The archived log files are
left in place indefinitely. Files not chosen here will not ever be rotated by cPanel software.

10.Zend Optimizer Installation
The Zend Optimizer™ boosts PHP performance by going over the intermediate code generated by
the standard Zend run-time compiler and optimizing it for faster execution. In addition, it runs the
files encoded by the Zend Guard, while enhancing the running speed of PHP applications.


11.Installed Xcache
root@server1 [~]# /scripts/phpextensionmgr list
Available Extensions:
EAccelerator
IonCubeLoader
Zendopt
Xcache
SourceGuardian
PHPSuHosin
