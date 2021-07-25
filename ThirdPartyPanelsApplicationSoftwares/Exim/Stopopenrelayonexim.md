---
title: Stop openrelay on exim
description: 
published: true
date: 2021-07-25T03:32:59.472Z
tags: 
editor: markdown
dateCreated: 2021-07-25T03:32:59.472Z
---

# Stop openrelay on exim

Telnet to yourmailserver at port 25 and issue all the following commands:

```
telnet hostname/ip 25
helo client.server.com
mail from: xxx@somedomain.com
rcpt to: yyy@somedomain.com
```

If you are getting the error “554 : Relay access denied” then the server is not an open Relay

If not Just pass the command “DATA” sfter the recipient and then enter the message ending with a period ie : “.”

If you get the reply “SUCCESS Relay Accepted – final response code 550″

Then as you feared your server is subjected to open relay and if not enjoy………. It is not

I hope your server is not open relay supporting, but if it is so, as it is a Cpanel Server you can stop it normally using the below scripts

```
/scripts/fixrelayd
/etc/rc.d/init.d/antirelayd restart
service exim restart
```

