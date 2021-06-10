---
title: Stop DDos/Syn attack
description: 
published: true
date: 2021-06-10T17:53:20.672Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:53:20.672Z
---

# How to stop DDOS/Syn attack


1.  Find.. to which IP address in the server is targeted by the ddos attack

```
netstat -plan  | grep  :80 | awk ‘{print $4}’ | cut -d: -f1 |sort |uniq -c
```

2. Find… from which IPs, the attack is coming

```
netstat -plan  | grep  :80 | awk ‘{print $5}’ | cut -d: -f1 |sort |uniq -c
```

In csf:

vi /etc/csf/csf.conf

SYNFLOOD is disabled by default. If you are not receiving any sort of attack, there is no need to enable it. If you are expecting an attack, enable it and set the rules a bit strict, like SYNFLOOD_RATE = “5/s” SYNFLOOD_BURST = “3″ my eg: SYNFLOOD = “1″ SYNFLOOD_RATE = “30/s” SYNFLOOD_BURST = “10″

SYNFLOOD

SYNFLOOD is disabled by default. If you are not receiving any sort of attack, there is no need to enable it. If you are expecting an attack, enable it and set the rules a bit strict, like

SYNFLOOD = “1″

SYNFLOOD_RATE = “30/s”

SYNFLOOD_BURST = “10″

i.e. if 30 connections are received from an IP/sec for 10 times, block it. Make sure don’t keep it too strict if you are not receiving an attack else it will generate false positives and will block legit connections.

PORTFLOOD

PORTFLOOD = 80;tcp;100;5,22;tcp;5;300

ie, If an IP makes 100 connections in 5 sec to port 80 (tcp), then it will be blocked from the server and if 5 connections in 300 sec to 22 port.

In /etc/sysctl.conf

Paste the following into the file, you can overwrite the current information.

#Kernel sysctl configuration file for Red Hat Linux

#For binary values, 0 is disabled, 1 is enabled. See sysctl(8) and

#sysctl.conf(5) for more details.

#Disables packet forwarding

net.ipv4.ip_forward=0

#Disables IP source routing

net.ipv4.conf.all.accept_source_route = 0

net.ipv4.conf.lo.accept_source_route = 0

net.ipv4.conf.eth0.accept_source_route = 0

net.ipv4.conf.default.accept_source_route = 0

#Enable IP spoofing protection, turn on source route verification

net.ipv4.conf.all.rp_filter = 1

net.ipv4.conf.lo.rp_filter = 1

net.ipv4.conf.eth0.rp_filter = 1

net.ipv4.conf.default.rp_filter = 1

#Disable ICMP Redirect Acceptance

net.ipv4.conf.all.accept_redirects = 0

net.ipv4.conf.lo.accept_redirects = 0

net.ipv4.conf.eth0.accept_redirects = 0

net.ipv4.conf.default.accept_redirects = 0

#Enable Log Spoofed Packets, Source Routed Packets, Redirect Packets

net.ipv4.conf.all.log_martians = 0

net.ipv4.conf.lo.log_martians = 0

net.ipv4.conf.eth0.log_martians = 0

#Disables IP source routing

net.ipv4.conf.all.accept_source_route = 0

net.ipv4.conf.lo.accept_source_route = 0

net.ipv4.conf.eth0.accept_source_route = 0

net.ipv4.conf.default.accept_source_route = 0

#Enable IP spoofing protection, turn on source route verification

net.ipv4.conf.all.rp_filter = 1

net.ipv4.conf.lo.rp_filter = 1

net.ipv4.conf.eth0.rp_filter = 1

net.ipv4.conf.default.rp_filter = 1

#Disable ICMP Redirect Acceptance

net.ipv4.conf.all.accept_redirects = 0

net.ipv4.conf.lo.accept_redirects = 0

net.ipv4.conf.eth0.accept_redirects = 0

net.ipv4.conf.default.accept_redirects = 0

#Disables the magic-sysrq key

kernel.sysrq = 0

#Decrease the time default value for tcp_fin_timeout connection

net.ipv4.tcp_fin_timeout = 15

#Decrease the time default value for tcp_keepalive_time connection

net.ipv4.tcp_keepalive_time = 1800

#Turn off the tcp_window_scaling

net.ipv4.tcp_window_scaling = 0

#Turn off the tcp_sack

net.ipv4.tcp_sack = 0

#Turn off the tcp_timestamps

net.ipv4.tcp_timestamps = 0

#Enable TCP SYN Cookie Protection

net.ipv4.tcp_syncookies = 1

#Enable ignoring broadcasts request

net.ipv4.icmp_echo_ignore_broadcasts = 1

#Enable bad error message Protection

net.ipv4.icmp_ignore_bogus_error_responses = 1

#Log Spoofed Packets, Source Routed Packets, Redirect Packets

net.ipv4.conf.all.log_martians = 1

#Increases the size of the socket queue (effectively, q0).

net.ipv4.tcp_max_syn_backlog = 1024

#Increase the tcp-time-wait buckets pool size

net.ipv4.tcp_max_tw_buckets = 1440000

#Allowed local port range

net.ipv4.ip_local_port_range = 16384 65536

Run /sbin/sysctl -p and sysctl -w net.ipv4.route.flush=1 to enable the changes without a reboot.

TCP Syncookies

echo 1 > /proc/sys/net/ipv4/tcp_syncookies

Some IPTABLES Rules:

```
iptables -A INPUT -p tcp –syn -m limit –limit 1/s –limit-burst 3 -j RETURN
 
iptables -A INPUT -p tcp –syn -m state –state ESTABLISHED,RELATED –dport 80 -m limit –limit 1/s –limit-burst 2 -j ACCEPT 

```
