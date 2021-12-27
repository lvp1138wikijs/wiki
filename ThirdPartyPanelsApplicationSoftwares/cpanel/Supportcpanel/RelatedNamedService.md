---
title: Related Named Service ( DNS )
description: 
published: true
date: 2021-12-27T18:12:30.756Z
tags: 
editor: markdown
dateCreated: 2021-12-27T18:12:30.756Z
---

# Related Named Service ( DNS )


## Checking the configuration of named.conf and zone files


The bind package has utilities to check the syntax of named.conf and any zone files. We can make use of thosebinaries to check our modifications done to those files before reloading or restarting named service.To check the sytax of zone file /var/named/domainname.com.db


[root@bash ~]# named-checkzone kb.com /var/named/domainname.com.db zone domainname.com/IN : loaded serial 2006032401OK
If everything is correct, it will show the serial number with which the zone file is loaded. Otherwise, it will giveerror message indicating the line number at which the error occured.To check the syntax of named.conf file,


[root@bash ~]# named-checkconf /etc/named.conf
You may also load the configuration of all master zones listed in named.conf at the time of checking the syntax as,


[root@bash ~]# named-checkconf -z /etc/named.conf
The command will show a detailed output in case any error in named.conf file.This way we can make sure that we are not editing the configuration file wrongly.

## Fixing rndc error in WHM/cPanel

(ndc: connection failed: connection refused)To get your name servers working, you will need to eliminate this error, itis quite a simple fix and can be completed in a few minutes via the standard cPanel /scripts

 

1. Login to your server as root via SSH

2. Run: /scripts/updatenow

3. Run: /scripts/fixndc

If not fixed then.

1. Login to your server as root via SSH

2. Run: vi /etc/rndc.conf

replace all instances of ―rndc -key with ―rndckey

3. Run: vi /etc/named.conf

replace all instances of ―rndc-key with ―rndckey

4. Run:/scripts/fixnamed

5. Run:/scripts/fixndc

6. If you received an error in the last step, run /scripts/fixndc another time.

7. Restart named
