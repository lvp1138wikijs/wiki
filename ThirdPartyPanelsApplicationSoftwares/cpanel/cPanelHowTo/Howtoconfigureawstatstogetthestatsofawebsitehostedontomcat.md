---
title: How to configure awstats to get the stats of a website hosted on tomcat (awstats)
description: 
published: true
date: 2021-12-23T19:24:13.233Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:24:13.233Z
---

# How to configure awstats to get the stats of a website hosted on tomcat (awstats)


**How to configure awstats to get the stats of a website hosted on tomcat (awstats)**.

**Issue**:

If a Customer is not using apache on a cpanel server and have installed a separate instance of tomcat to host his domains, the default awstats on cPanel will not generate the stats properly due to the change in the log formats of apache and tomcat. Referance: (ticket MGC-261-16107)



> apache(cPanel server) creates the logs on a single file.
> /usr/local/apache/domlogs/domain.com
> 
> NOTE: change domain.com with correct domain name.
{.is-info}


> tomcat creates separate access logs daily so the filename of the log file changes with date
> /home/tomcat/logs/access.2013-06-17.log
{.is-info}

**Solution**:

You can modify the awstats conf file to accept the tomcat logs.


> awstats conf :/home/admin/tmp/awstats/awstats.domain.com.conf
> 
> NOTE: change domain.com with correct domain name.
{.is-info}


- Edit the parameter "LogFile" in the awstats conf file as shown below.


```
LogFile="/home/tomcat/logs/access.%YYYY-0-%MM-0-%DD-0.log"
```

- Also setup a cronjob to update it manually. cpanel stats update will not update the stats for the domain.

```
/usr/local/cpanel/3rdparty/bin/awstats.pl -config=/home/admin/tmp/awstats/awstats.domain.com.conf -update
 
NOTE: change domain.com with correct domain name.
```

- The above command generate the awstats history filename as awstatsMMYYYY.txt instead of awstatsMMYYYY.muchoslibros.com.txt which is the default file for the cpanel for the Month MM and year YYYY. Replace it with the actual values.
- Since the history file was generated in another name we had to put the following script to update the stats for the domain. Create a file /root/updatestats.sh and put the following contents.

```
#!/bin/bash
/usr/local/cpanel/3rdparty/bin/awstats.pl -config=/home/admin/tmp/awstats/awstats.domainname.com.conf -update
rm -rf /home/admin/tmp/awstats/awstats`date +%m%Y`.domainname.com.txt
cp /home/admin/tmp/awstats/awstats`date +%m%Y`.txt /home/admin/tmp/awstats/awstats`date +%m%Y`.domainname.com.txt
chown user:user /home/admin/tmp/awstats/awstats`date +%m%Y`.domainname.com.txtNOTE: change domain.com with correct domain name and user with the actual username in the script.
```

- Execute the script every 10 minutes or 5 minutes using cron. If it is set to run once in a day, the stats will be updated only till the time when it is executed. For example: if it set to execute every day at 6 am, the stats will be updated till 6am, so execute it every 10 or 5 minutes  to avoid such issues.

```
*/10 * * * * /bin/sh /root/updatestats.sh
```

- Also note that cpanel stats update script /scripts/runweblogs still uses /usr/local/apache/domlogs/domain.com which will be empty, so it is better to disable the stat update for the domain from the cpanel.