---
title: New Website Account & Reseller
description: 
published: true
date: 2021-12-27T17:21:44.709Z
tags: 
editor: markdown
dateCreated: 2021-12-27T17:21:44.709Z
---

# New Website Account & Reseller

**Account Creation Failed**

While creating an account via WHM, you may get an error stating that, cannot create new user.

You can check the cPanel logs for the error.

tail -f /usr/local/cpanel/logs/error_log

Sometimes, you may get the following error.vipw lockfile (/etc/ptmp) is present!

This means that the useradd is locked. You will not be able to add new users unless you remove the following file.

You can also confirm it by executing the useradd command in the console. You will receive an error message statingthe above.

useradd user1

Check if this file is present.

ls -l /etc/ptmp

 /etc/ptmp >> This has a temporary copy of the password file. This file can be removed.rm -f /etc/ptmp

 
## Account Creation Failed

When trying to add a new domain in WHM, you may get an error like this.

Account Creation Status: failed
Sorry, a DNS entry for domainname.com already exists, please delete it first (from all servers in the dns cluster)
This means that a DNS Zone File already exists for this domain. Simply click to the "Delete a DNS Zone" link (in the WHM left-hand menu) and remove the domain name you are trying to add. Now you can reattempt the account creation.
or you can directly login to the server with root >> go to cd /var/named >> search the domainname.com.db file for which you were adding account and delete it.


##  Reseller list missing in WHM

This article discusses how to resolve issues where the WHM reseller list has disappeared however they still exist in
Apache‘s configuration and the users‘ directories still exist in /home

Solution -


1)/var/cpanel/users/
/var/cpanel/users/username should have the following syntax per line ―DNS=domain.com line. If not, ed
it this fileand change the line to DNS=domain.com
Secondly, be sure to check that the DNS zone above exists in ―Edit DNS Zone in WHM. If not, add it via ―AddDNS Zone in WHM.


2)/etc/httpd/conf/httpd.conf Double check that there is a VirtualHost container per domain in /var/named/


3)/etc/userdomains /etc/userdomains should have the following syntax per line ―domain.com: user where user is the reseller. If not, edit

this file and change the file to match


4)/etc/trueuserdomains /etc/trueuserdomains should
also have the following syntax per line ―domain.com:user where user is the domain
owner user.

If not:
mv /etc/trueuserowners /etc/trueuserowners1
 /scripts/updateuserdomains
 
## Account modification aborted, there was a problem changing the user name.

When you go to Account Functions >> Modify an Account and try to change the username of domain, sometimes you may get the following error.

 There is currently a configuration error in the Apache configuration file. User name change aborted. Account modification aborted, there was a problem changing the user name.

Solution

1) Login to WHM

2) Click on  Server Configuration >> Tweak Settings

3 ) Search “Max cPanel process memory”

4) choose “Unlimited”

5) Click on Save Button

6) Done

Now try to replace the username and I am sure that you can repalce or edit the username without any error.


 


 

