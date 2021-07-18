---
title: Send all outgoing email trough one IP address in postfix
description: 
published: true
date: 2021-07-18T05:08:17.591Z
tags: 
editor: markdown
dateCreated: 2021-07-18T05:08:17.591Z
---

# Send all outgoing email trough one IP address in postfix

> When a server has more then one IP address, then postfix will use all IP addresses randomly to send out emails. This can cause your emails to be listed as SPAM on other servers because the sending IP does not match the reverse IP of the server hostname. The solution is to bind postfix to the primary IP address of the server.
{.is-info}


For Sending all outgoing email trough one IP address in postfix, please do the following steps:

1.Edit the postfix main.cf file.

```
vi /etc/postfix/main.cf
```
2.Then add the below line.

```
smtp_bind_address = IP_Address
```
were IP_Address has to be replaced with the primary IP address of the server.

3.Then restart postfix using the following command:

```
/etc/init.d/postfix restart
```

Reference Ticket ID: VZE-951-49927



