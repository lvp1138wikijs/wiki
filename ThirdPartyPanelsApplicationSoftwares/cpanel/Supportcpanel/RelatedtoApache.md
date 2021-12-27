---
title: Related to Apache
description: 
published: true
date: 2021-12-27T18:17:35.560Z
tags: 
editor: markdown
dateCreated: 2021-12-27T18:17:35.560Z
---

# Related to Apache

## How to run apache & lighthttpd on port no.80


We need to have 2 IP in the server then only we can run both apache and lighthttpd on the same port. Assume that you have already installed both apache and lighthttpd.



Lighthttpd will help to increase the speed with a small memory consumption

Go to apache configuration and locate Listen directive

Here, Add ―Listen‖ directive to all  IP addresses of the server, except the IP for lighthttpd.
Listen IP_ADDRESS:80

Now, restart apache and then lighthttpd

You can try to access IP in browser and make sure both are listening on port 80

## Apache mod_userdir Protection ( Enabling & Disabling the Temp. URL to browse the websites )

Apache‘s mod_userdir allows users to view their sites by entering a tilde(~) and  their username as the URL on a specific host
For example http://serverip/domainname/~test/ will bring up the user test‘s domain.

The disadvantage of this feature is that any bandwidth usage used by this site will be put on the domain it is accessed under (in this case domainanme.com).
mod_userdir protection prevents this from happening.We can disable it on specific virtual hosts (generally shared ssl hosts).

Main >> Security Center >> Apache mod_userdir Tweak

## Auditing apache logs

The apache error logs are located on below path on a cpanel server

/usr/local/apache/logs/error_log

All exceptions caught by httpd, along with standard error output from CGI applications are logged here. The first place you should look when httpd crashes, or If you see errors while accessing a website

/usr/local/apache/logs/error_log





Now,

/usr/local/apache/logs/suexec_log

This log file contains auditing information reported by suexec each time a CGI application is executed. If you receive an internal server error, with no  relevant information being reported to the Apache  error_log, check here for potential suexec policy violations.

**How to check domain access logs**

 /usr/local/apache/domlogs/domain.com
 

## Apache Error , "Unable to Open Logs"

Sometimes apache  fails to start. It  shows  the error message in apache  error logs as

"Unable to Open Logs"

This is because of the low number of file descriptors. Check the current limit of file descriptors in the file /proc/sys/fs/file-max

$ cat /proc/sys/fs/file-max 
1024

If fs.file-max is quite small (several thousands or so), it should be changed to a higher value

$ echo “65535"> /proc/sys/fs/file-max

If you want this new value to be there permanently across reboots you can add it to /etc/sysctl.conf

# Maximum number of open files permitedfs.file-max = 65535

**To load new values from the sysctl.conf file**

$ sysctl -p /etc/sysctl.conf

**Trick - Add `ulimit -n 65536` command to /etc/init.d/httpd or /etc/init.d/httpd and /us r/sbin/apachectl apachestartup scripts at the top**


## What is mod_evasive ?

mod_evasive is an evasive maneuvers module for Apache to provide evasive action in the event of an HTTP DoS or DDoS attack or brute force attack. It is also designed to be a detection and network management tool, and can be easily configured to talk to ip chains, firewalls, routers, and etc... mod_evasive presently reports abuses via email and syslog facilities. 

Detection is performed by creating an internal dynamic hash table of IP Addresses and URLs, and denying any single IP address from any of the  following

- Requesting the same page more than a few times per second 
- Making more than 50 concurrent requests on the same child per second 
- Making any requests  while temporarily blacklisted (on a blocking list)

## Apache Failed to Start with Error Message as "No space left on Device"


If you receive the following error while restarting Apache in  the server, you need  to do the following steps.These errors means that there is no available IPC (inter-process communication) resources in the system, such as semaphores or shared memory segments. You need to  check IPC resources which are used in  the server using ‗ipcs‘
command:
$ ipcs -a
…
 
——Semaphore Arrays——–
 key semid owner perms nsems
 0×00000000 201293824 apache 600 1

You will be able to see a lot of semaphores under Apache . You need to kill those processes using the following script and restart apache.

 $ ipcs -s | grep apache | perl -e ‗while (<STDIN>) {@a=split(/\ s+/); print `ipcrm sem $a[1]`}‘

 
 $ service httpd restart
  
## How to increase the MaxClients value greater than the current HARD_SERVER_LIMIT set for Apache  
  
1. Check if there is any hard server limit.

/usr/local/apache/bin/httpd -V | gre p HARD_SERVER_LIMIT

2. Look for this directive in the Ap ache‘s header file /usr/local/apache/include/httpd.h

3. Edit this file and increase  the HARD_SERVER_LIMIT as per your requirement.

4. Recompile Apache using
/scripts/easyapache
5. There you will have an option to increase the Apache HARD_SERVER_LIMIT, since easyapache looks for the header files and sees the new value while build.

By default the MaxClients value will be 256.Once the build completes, you can see the new HARD_SERVER_LIMIT


## How to enable / disable suexec in WHM  
  
SuExec is an Apache feature that gives users the ability to run CGI and SSI programs using user IDs that are different from the user ID of the calling web server. This effectively means that CG I and SSI programs will not have access to the root account or have root permissions.

To Enable or Disable SuExec
  
- Click on the Enable/Disable SuExec link in the Server Setup menu in WHM
- Click on the Enable button to enable SuExec or click on the Disable button to disable SuExec  
  
suEXEC is based on a setuid wrapper program that is called by the main  Apache web server.
This wrapper is called when an HTTP request is made for a CGI or SSI program that the administrator has designated to run as auserid other than that of the main server. When such a request is made, Apache provides the suEXEC wrapper with the program‘s name and the user and  group IDs under which the program is  to execute.  