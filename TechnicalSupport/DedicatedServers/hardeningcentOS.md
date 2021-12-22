---
title: Hardening CentOS
description: 
published: true
date: 2021-12-22T13:18:22.721Z
tags: password policies, os policies, ddos deflate, ip tables, secure the ssh daemon
editor: markdown
dateCreated: 2021-12-22T13:18:22.721Z
---

# Hardening CentOS
Created by Xavier Sebastian, last modified on Jun 26, 2013
For hardening CentOS, please do the following steps:
## 1. Install useful packages such as tcpdump, mtr, zsh, perl and logrotate using the commands
## yum install tcpdump
#yum install mtr
#yum install zsh
#yum install perl
#yum install logrotate
###### 2. Setup automatic yum updates.
a. You can create daily or weekly updates with the following shell script.
/etc/cron.daily/yumupdate.sh to apply updates one a day.
/etc/cron.weekly/yumupdate.sh to apply updates once a week.
b. For more details about cron tab, click here
c. Sample shell script to update system
#!/bin/bash
YUM=/usr/bin/yum
$YUM -y -R 120 -d 0 -e 0 update yum
$YUM -y -R 10 -e 0 -d 0 update
where,
i. First command will update yum itself and next will apply system updates.
ii. -R 120 : Sets the maximum amount of time yum will wait before performing a command
iii. -e 0 : Sets the error level to 0 (range 0 - 10). 0 means print only critical errors about which you must
be told.
-d 0 : Sets the debugging level to 0 - turns up or down the amount of things that are printed. (range: 0
- 10).
iv. -y : Assume yes; assume that the answer to any question which would be asked is yes.
Note: Make sure you setup executable permission:
# chmod +x /etc/cron.daily/yumupdate.sh
## 3. Set password policies.
a. Passwords will expire every 180 days. In order to do that, please do the following command:
perl -npe 's/PASS_MAX_DAYS\s+99999/PASS_MAX_DAYS 180/' -i /etc/login.defs
b. Passwords may only be changed once a day. In order to do that, please do the following command:
perl -npe 's/PASS_MIN_DAYS\s+0/PASS_MIN_DAYS 1/g' -i /etc/login.defs
## 4. Set OS policies
a. Set idle users to be disconnected after 15 minutes. In order to do that, please do the following commands:
vi /etc/profile.d/os-security.sh
then add the following entries.
echo "Idle users will be removed after 15 minutes"
echo "readonly TMOUT=900" >> /etc/profile.d/os-security.sh
echo "readonly HISTFILE" >> /etc/profile.d/os-security.sh
Then make the file as executable using the command:
chmod +x /etc/profile.d/os-security.sh
vi /etc/profile.d/os-security.sh
then add the following entries.
echo "Idle users will be removed after 15 minutes"
echo "readonly TMOUT=900" >> /etc/profile.d/os-security.sh
echo "readonly HISTFILE" >> /etc/profile.d/os-security.sh
Then make the file as executable using the command:
chmod +x /etc/profile.d/os-security.sh
## 5. Install (if it is not installed) and configure IPTables firewall. (Please refer the article Secure Server Through IP
tables Rules for more details).
a. Open specified TCP/UDP ports.
b. Set rules to block common attacks.
i. Syn Floods.
ii. Fragmented Packets.
iii. Malformed XMAS Packets.
iv. Drop NULL packets.
v. Limit pings to 3 per second and bursts of 25.
vi. Discourage Port Scanning.
c. For more details, click here
d. Set up Connection Tracking.
## 6. Install DDoS Deflate.
a. More information about DDoS Deflate is available here
## 7. Install CHKROOTKIT.
a. Scheduled to check daily for issues and email your Admin Email.
b. More information about CHKROOTKIT is available here
## 8. Install rkhunter (Root Kit Hunter).
a. Scheduled to check daily for issues and email your Admin Email.
b. More information about rkhunter is available here
## 9. Install LSM (Linux Socket Monitor).
a. To install LSM, execute the following commands (as root):
wget http://www.r-fx.ca/downloads/lsm-current.tar.gz
md5sum lsm-current.tar.gz | cut -d ‘ ‘ -f1
Note:The md5sum should be d35ff3171cba48b5ed3127c7bb8dd1f0. If not, then delete the file and
download again.
tar -zxvf lsm-current.tar.gz
cd lsm-0.6
./installer.sh
cd ..
rm -rf lsm*
b. LSM is now installed. Next, we need to update the LSM base comparison files. To do this, execute the
command:
/usr/local/sbin/lsm -g
c. Next, edit /usr/local/lsm/conf.lsm as root. Find the line that reads:USER=”root” and change it to
USER=”[Fill in the email address to which LSM reports must be sent]".
d. Save the file and exit the editor.
e. Next, check for changes in sockets by executing the command: /usr/local/sbin/lsm -c as root. LSM will
check for unwanted sockets and send a report to the specified email address, if any are found.
## 10. Secure the SSH Daemon.
a. Change the SSH port to a random number.
b. Create an "admin" user.
c. Make it so only the "admin" user can be logged into over SSH.
## 11. In order to do that you can follow the steps specified at here.