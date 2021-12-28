---
title: Untitled Page
description: 
published: true
date: 2021-12-28T13:45:32.505Z
tags: essentials packages
editor: markdown
dateCreated: 2021-12-28T13:45:32.505Z
---

# Install Essentials Packages on CentOS/Fedora
Install them using Yum. Run the following commands

##### CentOS 6 & 7

`yum -y install net-utils net-snmp telnet net-snmp-utils whois emacs rsync \ 
htop jwhois hdparm munin-node ntfs-3g dstat mtr pciutils \
tree ncurses-devel ntfsprogs nbd traceroute zip tmpwatchm logrotate parted \
unzip gdisk e4fsprogs wget ebtables cronie perl-libwww-perl \
nmap bzip2 ntp nano dstat sysstat net-tools bind-utils smartmontools yum-utils`


##### CentOS 8

`yum -y install net-snmp telnet net-snmp-utils whois emacs rsync \
htop hdparm ntfs-3g dstat mtr pciutils \
tree ncurses-devel ntfsprogs traceroute zip logrotate parted \
unzip gdisk e4fsprogs wget ebtables cronie perl-libwww-perl \
nmap bzip2 nano dstat sysstat net-tools bind-utils smartmontools yum-utils`

