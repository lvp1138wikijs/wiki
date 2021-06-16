---
title: How to find Apache is using a lot of CPU?
description: 
published: true
date: 2021-06-16T17:51:19.502Z
tags: 
editor: markdown
dateCreated: 2021-06-16T17:51:19.502Z
---

**APPLIES TO**:

- Parallels Plesk for Linux/Unix

Resolution

Please enable this section in httpd.conf :


#Allow server status reports, with the URL of
http://servername/server-status
#Change the ".your-domain.com" to match your domain to enable.
#ExtendedStatus on
#<Location /server-status>
#SetHandler server-status
#Order deny,allow
#Deny from all
#Allow from .your-domain.com
#</Location

Then it will show what CGI script is producing a high load.

You can find more information here:

http://httpd.apache.org/docs-2.0/mod/mod_status.html

You can also make it password-protected:

ExtendedStatus on
<Location /server-status>
SetHandler server-status
AuthType basic
AuthName "Apache status"
AuthUserFile /etc/httpd/conf/server-status_htpasswd
Require valid-user
</Location

Then restart Apache.

 

 

Reference Ticket ID : ICJ-675-23031