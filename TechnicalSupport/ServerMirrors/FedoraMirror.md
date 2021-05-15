---
title: FedoraMirror
description: 
published: true
date: 2021-05-15T13:54:34.326Z
tags: 
editor: markdown
dateCreated: 2021-05-15T13:54:34.326Z
---

# Fedora Mirror
### Server Side

**Operating System**: CentOS

**Services**: Apache

**Tool used**: yum, rsync

**Plugin**: Yum Priority
**Step 01:**

Check apache service installed or not. If not then install it by running 

    yum install httpd

**Step 02:**
Create a new script named /usr/local/sbin/fedora-rsync.sh with following lines and  change ownership to root and permission to 755.

    touch /usr/local/sbin/fedora-rsync.sh
    chmod 755 /usr/local/sbin/fedora-rsync.sh
    chown root:root /usr/local/sbin/fedora-rsync.sh

Open it using your favorite editor and add the following codes to that file. 

#!/bin/sh
#
RSYNCROOT="rsync://mirrors.kernel.org/fedora/"
LOCKFILE="/var/lock/subsys/fedora-rsync"
IMGROOT="/var/www/html"
if [ -f $LOCKFILE ]; then
    echo "fedora-rsync.sh is already running."
    exit 0
fi
if [ -d $IMGROOT ]; then
    touch $LOCKFILE
    echo "----------"
    echo "Fedora 18"
    echo "----------"
    /usr/bin/rsync --progress -avSHPrt --delete --exclude "development" --exclude "releases/15" --exclude "releases/16" --exclude "releases/17" --exclude "releases/test" --exclude "updates/15" --exclude "updates/16" --exclude "updates/17"  --exclude "updates/19" $RSYNCROOT/ $IMGROOT
    chown -R root:root $IMGROOT/
    rm -f $LOCKFILE
else
    echo "Target directory $IMGROOT does not exist."
fi

Save the file
**Step 03:**

Run the mirror script.

    /usr/local/sbin/fedora-rsync.sh

It will take few hours to complete it. After that remove the apache test page and  restart apache service

    rm -rf /etc/httpd/conf.d/welcome.conf

    /etc/init.d/httpd restart
    chkconfig httpd on

Done.

Now load server main ip address in your browser to see files. 
Step 04:

Set corn to keep update mirror. Team Fedora suggested syncronize 2-4 times per day and this should be run via cron. Run command and add the following

    crontab -e

00 01 * * * /usr/local/sbin/fedora-rsync.sh > /dev/null 2> /dev/null
06 00 * * * /usr/local/sbin/fedora-rsync.sh > /dev/null 2> /dev/null
12 00 * * * /usr/local/sbin/fedora-rsync.sh > /dev/null 2> /dev/null
18 00 * * * /usr/local/sbin/fedora-rsync.sh > /dev/null 2> /dev/null

That's all with server side. 
### Client Side

Install yum priority plugin 

    yum install yum-priorities -y

Disable yum fastmirror priority plugin. Change 'Enable=0' in /etc/yum/pluginconf.d/fastestmirror.conf

Open fedora yum repositories and add the following to the top of repository files

    mirror-fedora.serverpoint.com - is our local fedora mirror website.

Open /etc/yum.repos.d/fedora.repo and modify it like the following

[fedora]
name=Fedora $releasever - $basearch
baseurl=http://mirror-fedora.serverpoint.com/releases/$releasever/Everything/$basearch/os/
mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=fedora-$releasever&arch=$basearch
enabled=1
#metadata_expire=7d
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-$basearch
priority=1

[fedora-debuginfo]
name=Fedora $releasever - $basearch
baseurl=http://mirror-fedora.serverpoint.com/releases/$releasever/Everything/$basearch/debug/
mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=fedora-debug-$releasever&arch=$basearch
enabled=0
metadata_expire=7d
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-$basearch
priority=1


[fedora-source]
name=Fedora $releasever - $basearch
baseurl=http://mirror-fedora.serverpoint.com/releases/$releasever/Everything/$basearch/source/SRPMS/
mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=fedora-source-$releasever&arch=$basearch
enabled=0
metadata_expire=7d
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-$basearch
priority=1

Then open /etc/yum.repos.d/fedora-updates.repo and modify it like the following

[updates]
name=Fedora $releasever - $basearch - Updates
failovermethod=priority
baseurl=http://mirror-fedora.serverpoint.com/updates/$releasever/$basearch/
mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=updates-released-f$releasever&arch=$basearch
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-$basearch
priority=1


[updates-debuginfo]
name=Fedora $releasever - $basearch - Updates - Debug
failovermethod=priority
baseurl=http://mirror-fedora.serverpoint.com/updates/$releasever/$basearch/debug/
mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=updates-released-debug-f$releasever&arch=$basearch
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-$basearch
priority=1

[updates-source]
name=Fedora $releasever - Updates Source
failovermethod=priority
baseurl=http://mirror-fedora.serverpoint.com/updates/$releasever/SRPMS/
mirrorlist=https://mirrors.fedoraproject.org/metalink?repo=updates-released-source-f$releasever&arch=$basearch
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-fedora-$basearch
priority=1

Then run following commands

    yum clean all
    yum update

That's all.