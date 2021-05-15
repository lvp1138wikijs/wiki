---
title: CentOS Mirror 
description: 
published: true
date: 2021-05-15T13:47:26.207Z
tags: 
editor: markdown
dateCreated: 2021-05-15T13:47:26.207Z
---

# CentOS Mirror 
### Server Side

**Operating System**: CentOS

**Services**: Apache

**Tool used**: yum, rsync

**Plugin**: Yum Priority
**Step 01:
**
Check apache service installed or not. If not then install it by running 

    yum install httpd

**Step 02:
**
Create a new script named /usr/local/sbin/centos-rsync.sh. Change ownership to root and permission to 755

    This is good script. I used this same logic in other mirrors too. I found it from internet, just modified the values as per http://www.centos.org/modules/tinycontent/index.php?id=22

    touch /usr/local/sbin/centos-rsync.sh
    chmod 755 /usr/local/sbin/centos-rsync.sh
    chown root:root /usr/local/sbin/centos-rsync.sh

Open it using your favorite editor and add the following codes to that file. 

#!/bin/sh
#
RSYNCROOT="us-msync.centos.org::CentOS"
LOCKFILE="/var/lock/subsys/centos-rsync"
IMGROOT="/var/www/html"

if [ -f $LOCKFILE ]; then
echo "centos-rsync.sh is already running."
exit 0
fi

if [ -d $IMGROOT ]; then
touch $LOCKFILE

echo "----------"
echo "CentOS Mirror"
echo "----------"
/usr/bin/rsync --progress -avSHPrt --delete --exclude "mirrorscripts" $RSYNCROOT $IMGROOT

chown -R root:root $IMGROOT/
rm -f $LOCKFILE
else
echo "Target directory $IMGROOT does not exist."
fi

Now save the file.

**Step 03:**
Run the mirror script.

    /usr/local/sbin/centos-rsync.sh

It will take few hours to complete it. After that remove the apache test page and  restart apache service

    rm -rf /etc/httpd/conf.d/welcome.conf

    /etc/init.d/httpd restart
    chkconfig httpd on

Done.

Now load server main ip address in your browser to see files. 
**Step 04:**

Set corn to keep update mirror. Team CentOS suggested syncronize 2-4 times per day and this should be run via cron. Run command and add the following

    crontab -e

00 01 * * * /usr/local/sbin/centos-rsync.sh > /dev/null 2> /dev/null
06 00 * * * /usr/local/sbin/centos-rsync.sh > /dev/null 2> /dev/null
12 00 * * * /usr/local/sbin/centos-rsync.sh > /dev/null 2> /dev/null
18 00 * * * /usr/local/sbin/centos-rsync.sh > /dev/null 2> /dev/null


That's all with server side. 

### Client Side

Install yum priority plugin 

    centos 5: yum install yum-plugin-priorities -y

    centos 6: yum install yum-priorities -y

Disable yum fastmirror priority plugin. Change 'Enable=0' in /etc/yum/pluginconf.d/fastestmirror.conf

Go to /etc/yum.repos.d and open CentOS-Base.repo and modify it like the following

    mirror-centos.serverpoint.com - is our local centos mirror website.

[base]
name=CentOS-$releasever - Base
baseurl=http://mirror-centos.serverpoint.com/$releasever/os/$basearch/
mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5
priority=1
failovermethod=priority

[updates]
name=CentOS-$releasever - Updates
baseurl=http://mirror-centos.serverpoint.com/$releasever/updates/$basearch/
mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5
priority=1
failovermethod=priority

[extras]
name=CentOS-$releasever - Extras
baseurl=http://mirror-centos.serverpoint.com/$releasever/extras/$basearch/
mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5
priority=1
failovermethod=priority

[centosplus]
name=CentOS-$releasever - Plus
baseurl=http://mirror-centos.serverpoint.com/$releasever/centosplus/$basearch/
mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5
priority=1
failovermethod=priority

[contrib]
name=CentOS-$releasever - Contrib
baseurl=http://mirror-centos.serverpoint.com/$releasever/contrib/$basearch/
mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5
priority=1
failovermethod=priority

Then run following commands

    yum clean all
    yum update

That's all.