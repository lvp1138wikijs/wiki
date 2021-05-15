---
title: Ubuntu Mirror
description: 
published: true
date: 2021-05-15T13:57:44.619Z
tags: 
editor: markdown
dateCreated: 2021-05-15T13:57:44.619Z
---

# Ubuntu Mirror
### Server Side

**Operating System**: CentOS

**Services**: Apache

**Tool used**: yum, rsync
**Step 01:**

Check apache service installed or not. If not then install it by running 

    yum install httpd

**Step 02:**

Create a new script named /usr/local/sbin/ubuntu-rsync.sh. Change ownership to root and permission to 755

    touch /usr/local/sbin/ubuntu-rsync.sh
    chmod 755 /usr/local/sbin/ubuntu-rsync.sh
    chown root:root /usr/local/sbin/ubuntu-rsync.sh

Open it using your favorite editor and add the following codes to that file. The script is taken from https://help.ubuntu.com/community/Rsyncmirror

## Mirror Synchronization Script /usr/local/bin/ubuntu-mirror-sync.sh
## Version 1.01 Updated 13 Feb 2007 by Peter Noble
## Point our log file to somewhere and setup our admin email
log=/var/log/mirrorsync.log
adminmail=admin@my.domain
# Set to 0 if you do not want to receive email
sendemail=1
# Subject is the subject of our email
subject="Ubuntu Mirror Sync Finished"
## Setup the server to mirror
remote=rsync://archive.ubuntu.com/ubuntu
## Setup the local directory / Our mirror
local=/media/mirror/ubuntu
## Initialize some other variables
complete="false"
failures=0
status=1
pid=$$
echo "`date +%x-%R` - $pid - Started Ubuntu Mirror Sync" >> $log
while [[ "$complete" != "true" ]]; do
        if [[ $failures -gt 0 ]]; then
                ## Sleep for 5 minutes for sanity's sake
                ## The most common reason for a failure at this point
                ##  is that the rsync server is handling too many concurrent connections.
                sleep 5m
        fi
        if [[ $1 == "debug" ]]; then
                echo "Working on attempt number $failures"
                rsync -a --delete-after --progress $remote $local
                status=$?
        else
                rsync -a --delete-after $remote $local >> $log
                status=$?
        fi
        
        if [[ $status -ne "0" ]]; then
                complete="false"
                (( failures += 1 ))
        else
                echo "`date +%x-%R` - $pid - Finished Ubuntu Mirror Sync" >> $log
                # Send the email
                if [[ -x /usr/bin/mail && "$sendemail" -eq "1" ]]; then
                mail -s "$subject" "$adminmail" <<OUTMAIL
Summary of Ubuntu Mirror Synchronization
PID: $pid
Failures: $failures
Finish Time: `date`
Sincerely,
$HOSTNAME
OUTMAIL
                fi
        complete="true"
        fi
done
exit 0

Save it
Step 03:

Run the mirror script.

    /usr/local/sbin/ubuntu-rsync.sh

It will take few hours to complete it. After that remove the apache test page and  restart apache service

    rm -rf /etc/httpd/conf.d/welcome.conf

    /etc/init.d/httpd restart
    chkconfig httpd on

Done.

Now load server main ip address in your browser to see files. 
Step 04:

Set corn to keep update mirror. Official Ubuntu Mirrors are recommended to update their mirrors every 6 hours and this should be run via cron. Run command and add the following

    crontab -e

00 01 * * * /usr/local/sbin/ubuntu-rsync.sh > /dev/null 2> /dev/null
06 00 * * * /usr/local/sbin/ubuntu-rsync.sh > /dev/null 2> /dev/null
12 00 * * * /usr/local/sbin/ubuntu-rsync.sh > /dev/null 2> /dev/null
18 00 * * * /usr/local/sbin/ubuntu-rsync.sh > /dev/null 2> /dev/null


That's all with server side. 
Client Side
Configuration

Open debian repository file /etc/apt/sources.list  using your favorate editor

    mirror-ubuntu.serverpoint.com - is our local centos mirror website.

Code Name

The value 'quantal' is the code name of ubuntu version 12.10 installed on the client server. If customer installed another version of ubuntu then that value will be changed.

deb http://mirror-ubuntu.serverpoint.com quantal main
deb http://mirror-ubuntu.serverpoint.com quantal-updates main
deb http://mirror-ubuntu.serverpoint.com quantal-security main
deb http://mirror-ubuntu.serverpoint.com quantal universe
deb http://mirror-ubuntu.serverpoint.com quantal-updates universe

deb http://archive.ubuntu.com/ubuntu quantal main
deb http://archive.ubuntu.com/ubuntu quantal-updates main
deb http://security.ubuntu.com/ubuntu quantal-security main
deb http://archive.ubuntu.com/ubuntu quantal universe
deb http://archive.ubuntu.com/ubuntu quantal-updates universe

Set priority on Repositories

The preference control file for APT is /etc/apt/preferences. Modify it to setup priority on selected repositories. If that file not exist then just create it.

    touch /etc/apt/preferences

The default Pin-Priority is 500, everything exceeding 500 will be prioritized.

Open /etc/apt/preferences add the following

    Package: *
    Pin: origin mirror-ubuntu.serverpoint.com
    Pin-Priority: 700

To view the priorities run command

    apt-cache policy package_name

Then run following commands

    apt-get clean all
    apt-get update

That's all. If our mirror failed in case then it will use the public one.