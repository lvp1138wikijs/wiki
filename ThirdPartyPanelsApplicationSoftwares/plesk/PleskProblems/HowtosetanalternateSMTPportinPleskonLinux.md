---
title: How to set an alternate SMTP port in Plesk on Linux
description: 
published: true
date: 2021-07-18T04:46:37.331Z
tags: 
editor: markdown
dateCreated: 2021-07-18T04:46:37.331Z
---

In order to set an alternate SMTP port in Plesk on Linux, please do the following steps:

1) Login to the server as root user via SSH.

2) A new entry will need to be created in xinetd for the alternate port:

```
cd /etc/xinetd.d

cp smtp_psa smtp_psa_p26
```

3) Open the file "smtp_psa_p26"  using vi editor and add the following line.

```
vi smtp_psa_p26
```
Make the first line say “service smtp_p26” and save the file.

4) Next edit the services for the system to include the newly created one.

```
vi /etc/service
```

5) Then make entries like bellow.

```
smtp_p26 26/tcp mail
smtp_p26 26/udp mail
```
6) Restart xinetd and the server should be listening on port 26. 

7) You van use the below command to verify the changes:

```
netstat -lpn|grep 26
```



