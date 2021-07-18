---
title: How to set an alternate SMTP port in Plesk on QMail and Postfix
description: 
published: true
date: 2021-07-18T04:52:06.906Z
tags: 
editor: markdown
dateCreated: 2021-07-18T04:52:06.906Z
---

# How to set an alternate SMTP port in Plesk on QMail and Postfix

**QMail** (Parallels Plesk Panel 8.x, 9.x)

1) Login to the server as root user via SSH.

2) Choose any unused port and add it to the **/etc/services** file.

```
smtp_alt 25025/tcp # new SMTP port
```

3) If you have 'xinetd'  as a super-server,  make a copy of **/etc/xinetd.d/smtp_psa** to **/etc/xinetd.d/smtp_psa_alt** and correct the service line within the new file:


```
service smtp_alt
```

4) Restart xinetd using the following command:

```
/etc/init.d/xinetd restart
```
5) You may also need to reconfigure Horde IMP (webmail) settings so they also use the alternative SMTP port.This can be done in **/etc/psa-horde/imp/servers.php** file under the **smtpport** parameter for both IMAP and POP3 servers.

 6) If you have a 'netd' super-server (Debian or FreeBSD), modify **inetd.conf** to enable an additional SMTP port:

```
grep '^smtp ' /etc/inetd.conf | sed 's/^smtp/smtp_alt/' >> /etc/inetd.conf
```

7) Then restart inetd.

=======================================

**Postfix** (Parallels Plesk Panel 9.x, 10.x, ...)

1) Add the following line to the Postfix configuration file **/etc/postfix/master.cf** :

```
<IP_Address>:<port> inet n - n - - smtpd
```

where <IP_Address> is the IP address of your server and port is the additional port for the SMTP connection.

2) If Postfix is configured to use **Postfix Before-Queue Content Filter** extend the line with the proxy filter settings:

```
<IP_Address>:<port> inet n - - - - smtpd -o smtpd_proxy_filter=127.0.0.1:10025
```

3) Reload the mail service with **mailmng** after the reconfiguration:

```
# /usr/local/psa/admin/sbin/mailmng --reload-service

Reloading postfix: [  OK  ]
```

