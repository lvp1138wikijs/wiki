---
title: How to assign a dedicated IP to a Sub-domain OR Add-on/Park domain
description: 
published: true
date: 2021-12-23T19:16:23.329Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:16:23.328Z
---

# How to assign a dedicated IP to a Sub-domain OR Add-on/Park domain

By default, cPanel allows one IP per account, however in case you wish to assign multiple IPs to a Sub-domain, please do the following steps:

1) Open /var/cpanel/userdata/<username>/ directory which is a sub-domain related file using vi editor, and then change the value of "IP" to a dedicated IP and save file.The add-on and Park domains have their related subdomain files in the same directory.

 2) Rebuild the apache configuration for the changes to take affect in the respective VirtualHost entry using the following commands.

```
/scripts/rebuildhttpdconf
```

3) Restart apache webserver.

```
service httpd restart
```
  
4) Add the dedicated IP and sub-domain in the /etc/domainips file to mark the dedicated IP as assigned so WHM won’t be able to assign it to other domains.
  
```
dedicatedIP: subdomain.domain.tld
```
  
5) save the file and rebuild the IP pool using the following command:

```
/scripts/rebuildippool
```
  
6) Edit the DNS zone file of the main domain (i.e. the domain under which the sub-domain is created) using vi editor and add an ‘A’ record for the sub-domain to point to the new IP.
  
```
vi /var/named/domain.tld.db
```
  
7) Then restart the "named" service using the following command:

```
service named restart
```

Allow sometime for the new IP to propagate.

  