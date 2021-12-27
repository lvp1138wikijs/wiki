---
title: Error with frontpage extension in cpanel
description: 
published: true
date: 2021-12-27T15:23:55.055Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:23:55.055Z
---

# Error with frontpage extension in cpanel

If the customer is getting the following error in FrontPage Extensions Admin panel

After logging in to Frontpage:

Tools --> Server --> Administration Home

```
Server Error: Unknown web server type "WebServerX".
```

It could be due to some misconfiguration in the mod_security. Follow the steps to fix it.

1) Check if mod_security is installed on the server.  If so check  mod_security configuration file.

```
$vi  /usr/local/apache/conf/mod_security.conf
```

2) Search for the following line in the configuration file.

```
# Server masking is optional
SecServerSignature "WebServerX"
```

3) Comment  the following line  and save the file.

```
#SecServerSignature "WebServerX"
```
4) Now restart apache

```
/scripts/restartsrv httpd
```

Now retry connecting to the Frontpage and check the Admin panel, it should be loading fine.


