---
title: Related to cPanel/WHM/Webmail Logins
description: 
published: true
date: 2021-12-27T18:25:43.257Z
tags: 
editor: markdown
dateCreated: 2021-12-27T18:25:43.257Z
---

# Related to cPanel/WHM/Webmail Logins

## 404 error on /whm /cpanel /webmail


The following URLs giving 404 error

````
http://<IP address>/whm

http://<IP address>/cpanel

http://<IP address>/webmail
````

Check if the following file is present on the server. Also make sure that the file permissions and ownerships are correct.

```
/usr/local/cpanel/cgi-sys/whmredirect.cgi
```

**Error message**

```
[Sun Jun 11 00:58:02 2006] [error] (13)Permission denied: exec of /usr/local/cpanel/cgi-sys/redirect.cgi failed
[Sun Jun 11 00:58:02 2006] [error] [client 70.31.76.95] Premature end of script headers: /usr/local/cpanel/cgi-sys/redirect.cgi
```

**permissions and ownership of the file**.

```
-rwxr-xr-x 1 root wheel 915 Nov 21 2004 /usr/local/cpanel/cgi-sys/redirect.cgi*
```

*error messages and the file permissions from cPanel forums

## 404 Error with cPanel Proxy domain

Some time you will get 404 pages while access whm/cpanel/webmail via whm.domain.com / cpanel.domain.com. It may be an issue with proxy domain settings with cPanel. You can try to run the following command to fix it.

```
/scripts/proxydomains --domain=domain.com add
```

## Horde login error

If you are getting Horde login error in Cpanel like :

Warning: Unknown: write failed: Disk quota exceeded (122) in Unknown on line 0Warning: Unknown: Failed to write session data (files). Please verify that the current setting of session.save_path is correct (/var/cpanel/userhomes/cpanelhorde/sessions) in Unknown on line 0

 

Then try this Cpanel script :

/scripts/autorepair phpapps_owner_fix

 

The above script will reset all the quotas for the Cpanel* users.

## DB Error: connect failed in horde

**When try to access the Horde from cPanel  then it shows following error**.

```
Warning: fopen(/var/cpanel/horde/log/horde_0.log) [function.fopen]: failed to open stream: Permission denied in /usr/local/cpanel/3rdparty/lib/php/Log/file.php on line 216
A fatal error has occurred

DB Error: connect failed

Details have been logged for the administrator.
```

**Solution**:

The problem due to the ” Horde Groupware Webmail Edition detected ” means when you have try to update the Horde by using following commands

root@server[~]# /usr/local/cpanel/bin/update-horde --force

Then it shows the following error

```
!!!     Horde Groupware Webmail Edition detected        !!!
Install or update of standard Horde Webmail is disabled.
Horde Groupware Webmail was installed with cPanel 11.25.1.
Downgrades of Horde are not permitted due to MySQL differences.
```
Then you need to move the file

root@server[~]# mv /var/cpanel/horde/groupware_version /var/cpanel/horde/groupware_version-bak

After that run following commands

root@server[~]# /usr/local/cpanel/bin/update-horde --force

Done

Now horde is updated and reset and you can able to access it without any problem.

 
## Template Error: The template file must be given 

**Error : Template Error: The template file must be given**

**Solution** :

The problem due the cpanel default page missing on the server so you can reset the default page setting by using following steps …

**WHM Main >> Account Functions >> Web Template Editor >  Revert to Default**

Once done you will again see the cpanel default page.

If you are facing this error on number of domains then you need to add the apache conf entry for that domain  manually into **httpd.conf** file.
 
