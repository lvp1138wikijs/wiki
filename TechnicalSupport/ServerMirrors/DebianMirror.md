---
title: Debian Mirror 
description: 
published: true
date: 2021-05-15T13:52:28.032Z
tags: 
editor: markdown
dateCreated: 2021-05-15T13:52:28.032Z
---

# Debian Mirror 
### Server Side

**Operating System**: CentOS

**Services**: Apache

**Tool used**: yum, rsync
**Step 01**:

Check apache service installed or not. If not then install it by running 

    yum install httpd

**Step 02:**

Create a new script named /usr/local/sbin/debian-rsync.sh. Change ownership to root and permission to 755

    touch /usr/local/sbin/debian-rsync.sh
    chmod 755 /usr/local/sbin/debian-rsync.sh
    chown root:root /usr/local/sbin/debian-rsync.sh

Open it using your favorite editor and add the following codes to that file. 

#!/bin/sh
#
RSYNCROOT="ftp.us.debian.org::debian"
LOCKFILE="/var/lock/subsys/debian-rsync"
IMGROOT="/var/www/html"
if [ -f $LOCKFILE ]; then
    echo "debian-rsync.sh is already running."
    exit 0
fi
if [ -d $IMGROOT ]; then
    touch $LOCKFILE
    echo "----------"
    echo "Debian Mirror"
    echo "----------"
    /usr/bin/rsync --progress -avSHPrt  --delete  $RSYNCROOT $IMGROOT
    chown -R root:root $IMGROOT/
    rm -f $LOCKFILE
else
    echo "Target directory $IMGROOT does not exist."
fi

Now save the file.
**Step 03:**

Run the mirror script.

    /usr/local/sbin/debian-rsync.sh

It will take few hours to complete it. After that remove the apache test page and  restart apache service

    rm -rf /etc/httpd/conf.d/welcome.conf

    /etc/init.d/httpd restart
    chkconfig httpd on

Done.

Now load server main ip address in your browser to see files. 
Step 04:

Set corn to keep update mirror. Team Debian suggested syncronize 2-4 times per day and this should be run via cron. Run command and add the following

    crontab -e

00 01 * * * /usr/local/sbin/debian-rsync.sh > /dev/null 2> /dev/null
06 00 * * * /usr/local/sbin/debian-rsync.sh > /dev/null 2> /dev/null
12 00 * * * /usr/local/sbin/debian-rsync.sh > /dev/null 2> /dev/null
18 00 * * * /usr/local/sbin/debian-rsync.sh > /dev/null 2> /dev/null


That's all with server side. 
### Client Side
**Configuration**

Open debian repository file /etc/apt/sources.list  using your favorate editor

    mirror-debian.serverpoint.com - is our local centos mirror website.

Code Name

squeeze = The code name of Debian 6.

The value 'squeeze' is the code name of Debian 6 which is installed on the client server. If customer installed another version of debian then that code name will be changed.

 You can see correct code in /etc/apt/sources.list. Note that code name and modify repository file respectively.

#Main
deb http://mirror-debian.serverpoint.com squeeze main
deb http://http.us.debian.org/debian squeeze main
deb-src http://mirror-debian.serverpoint.com squeeze main


#Update
deb http://mirror-debian.serverpoint.com squeeze-updates main
deb http://security.debian.org/ squeeze/updates main
deb-src http://mirror-debian.serverpoint.com squeeze-updates main

**Set priority on Repositories **
The preference control file for APT is /etc/apt/preferences. Modify it to setup priority on selected repositories. If that file not exist then just create it.

    touch /etc/apt/preferences

The default Pin-Priority is 500, everything exceeding 500 will be prioritized.

Open /etc/apt/preferences add the following

    Package: *
    Pin: origin mirror-debian.serverpoint.com
    Pin-Priority: 700

To view the priorities run command

    apt-cache policy package_name


    # apt-cache policy links
    links:
     Installed: 2.3~pre1-1+squeeze1
     Candidate: 2.3~pre1-1+squeeze1
     Version table:
     *** 2.3~pre1-1+squeeze1 0
     700 http://mirror-debian.serverpoint.com/ squeeze/main amd64 Packages
     500 http://http.us.debian.org/debian/ squeeze/main amd64 Packages
     100 /var/lib/dpkg/status

Then run following commands

    apt-get clean all
    apt-get update

That's all. If our mirror failed in case then it will use the public one.