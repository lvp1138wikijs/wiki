---
title: Iptables Rules for cPanel
description: 
published: true
date: 2021-12-27T16:50:53.262Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:50:53.262Z
---

# Iptables Rules for cPanel


```
# Clear rules
iptables -t filter -F
iptables -t filter -X
echo - Clear rules : [OK]
# SSH In
iptables -t filter -A INPUT -p tcp --dport 22 -j ACCEPT
echo - SSH : [OK]
# Don't break established connections
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
echo - established connections : [OK]
# Block all connections by default
iptables -t filter -P INPUT DROP
iptables -t filter -P FORWARD DROP
iptables -t filter -P OUTPUT DROP
echo - Block all connections : [OK]
# Loopback
iptables -t filter -A INPUT -i lo -j ACCEPT
iptables -t filter -A OUTPUT -o lo -j ACCEPT
echo - Loopback : [OK]
# ICMP (Ping)
iptables -t filter -A INPUT -p icmp -j ACCEPT
iptables -t filter -A OUTPUT -p icmp -j ACCEPT
echo - PING : [OK]
# DNS In/Out
iptables -t filter -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -t filter -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 53 -j ACCEPT
iptables -t filter -A INPUT -p udp --dport 53 -j ACCEPT
echo - DNS : [OK]
# NTP Out
iptables -t filter -A OUTPUT -p udp --dport 123 -j ACCEPT
echo - NTP : [OK]
# FTP Out
iptables -t filter -A OUTPUT -p tcp --dport 20:21 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 30000:50000 -j ACCEPT
# FTP In
iptables -t filter -A INPUT -p tcp --dport 20:21 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 30000:50000 -j ACCEPT
iptables -t filter -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
echo - FTP : [OK]
# HTTP + HTTPS Out
iptables -t filter -A OUTPUT -p tcp --dport 80 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 443 -j ACCEPT
# HTTP + HTTPS In
iptables -t filter -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 443 -j ACCEPT
echo - HTTP/HTTPS : [OK]
# Mail SMTP:25
iptables -t filter -A INPUT -p tcp --dport 25 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 25 -j ACCEPT
echo - SMTP : [OK]
# Mail SUBMISSION:587
iptables -t filter -A INPUT -p tcp --dport 587 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 587 -j ACCEPT
echo - SUBMISSION : [OK]
# Mail SMTPS:465
iptables -t filter -A INPUT -p tcp --dport 465 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 465 -j ACCEPT
echo - SMTPS : [OK]
# Mail POP3:110
iptables -t filter -A INPUT -p tcp --dport 110 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 110 -j ACCEPT
echo - POP : [OK]
# Mail POPS3:995
iptables -t filter -A INPUT -p tcp --dport 995 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 995 -j ACCEPT
echo - POPS : [OK]
# Mail IMAP:143
iptables -t filter -A INPUT -p tcp --dport 143 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 143 -j ACCEPT
echo - IMAP : [OK]
# Mail IMAPS:993
iptables -t filter -A INPUT -p tcp --dport 993 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 993 -j ACCEPT
echo - IMAPS : [OK]
# CPANEL + WHM
iptables -t filter -A INPUT -p tcp --dport 2082:2083 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 2082:2083 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 2086:2087 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 2086:2087 -j ACCEPT
iptables -t filter -A INPUT -p tcp --dport 2095:2096 -j ACCEPT
iptables -t filter -A OUTPUT -p tcp --dport 2095:2096 -j ACCEPT
echo - CPANEL + WHM : [OK]
echo - Firewall : [OK]
#save iptables
service iptables save
echo - Firewall Saved : [OK]
#restart firewall
service iptables restart
echo - Firewall restarted : [OK]
```