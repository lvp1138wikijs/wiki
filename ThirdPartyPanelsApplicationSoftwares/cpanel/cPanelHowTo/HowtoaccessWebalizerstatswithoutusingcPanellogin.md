---
title: How to access Webalizer stats without using cPanel login.
description: 
published: true
date: 2021-12-23T19:13:10.683Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:13:10.683Z
---

# How to access Webalizer stats without using cPanel login.


In order to access the webalizer stats without using cPanel login, please do the following steps.

1) Login to WHM as root.  Using “List Accounts“, find the cPanel account for the user you are working with and click the cPanel icon.

2) On cpanel, click on "Subdomains” icon and then add stats.whateverdomain.com as subdomain.

3) Once created the subdomain, leave cPanel and log in to your account via SSH as root user.

4) Then go to the user’s “stats” subdirectory under the public_html directory.

```
cd /home/username/public_html/stats
```

5) Then edit the .htaccess file using vi editor and add the line Options +FollowSymLinks and save it. It will ensure that Apache will follow system symlinks for the site.

6) Now create a symlink between the webalizer directory and a new “folder” we’ll call “webalizer” to keep it simple:

```
ln -s ../../tmp/webalizer webalizer
```

7) Now change the ownership of the webalizer link to the cPanel user this account belongs to.

```
chown -h username:username webalizer
```

8) Then change the webalizer folder permission to 755.

```
chmod 755 ../../tmp/webalizer
```

9) Then exit SSH and go back to user cPanel account.

10) In cPanel,use “Password Protect Directories” button, navigate to the “public_html/stats/webalizer” directory you just created, then password protect the directory and create a username and password that is different from the cPanel name and password.  This will be the username and password that you will give to your end user.

11) Now the user will be able to access webalizer stats using http://stats.domainname.com/webalizer using separate username and password.

