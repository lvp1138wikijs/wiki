---
title: Hotmail Blacklist Issues
description: 
published: true
date: 2021-03-10T00:24:20.661Z
tags: 
editor: markdown
dateCreated: 2021-03-10T00:24:20.661Z
---

# Hotmail Blacklist Issues


When a customer complains that he cannot send emails to hotmail ask him to provide us with the full email header of his bounced emails.

For example:

```
This message was created automatically by mail delivery software.
A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:
kreyes_o@hotmail.com
SMTP error from remote mail server after MAIL FROM:<test@chefpersonal.com.mx> SIZE=1659:
host mx1.hotmail.com [65.55.92.152]: 550 SC-001 (SNT0-MC2-F8) Unfortunately, messages from 64.235.48.216 weren't sent. Please contact your Internet service provider since part of their network is on our block list. You can also refer your provider tohttp://mail.live.com/mail/troubleshooting.aspx#errors.

------ This is a copy of the message, including all the headers. ------

Return-path: <test@chefpersonal.com.mx>
Received: from localhost ([127.0.0.1]:58106 helo=chefpersonal.com.mx)
by dn1.fabricadesoluciones.com with esmtpa (Exim 4.80.1)
(envelope-from <test@chefpersonal.com.mx>)
id 1Ut3oO-00034X-0f
for kreyes_o@hotmail.com; Sat, 29 Jun 2013 15:40:08 -0700
MIME-Version: 1.0
Content-Type: text/plain; charset=UTF-8;
format=flowed
Content-Transfer-Encoding: 7bit
Date: Sat, 29 Jun 2013 15:40:07 -0700
From: test@chefpersonal.com.mx
To: <kreyes_o@hotmail.com>
Subject: Test Chef
Message-ID: <1753e2334c641be8c3d3a1954147ee07@chefpersonal.com.mx>
X-Sender: test@chefpersonal.com.mx
User-Agent: Roundcube Webmail/0.8.5
```

**From the header message we can understand the cause of the issue:**


```
SMTP error from remote mail server after MAIL FROM:<test@chefpersonal.com.mx> SIZE=1659:
host mx1.hotmail.com [65.55.92.152]: 550 SC-001 (SNT0-MC2-F8) Unfortunately, messages from 64.235.48.216 weren't sent. Please contact your Internet service provider since part of their network is on our block list. You can also refer your provider tohttp://mail.live.com/mail/troubleshooting.aspx#errors.
```

The client  is unable to send emails because his IP address  is in the blocklist of hotmail.

We will first have to check the Serverpoint's gmail account and check whether he has any recent abuse issues.

If there are any recent abuse issues those have to be cleared first before contacting hotmail to delist his IP.

Once everything is clear he will have to contact hotmail to delist his IP.



Hotmail will ask for certain information, like your domain name, type of emails you sent and sample emails etc. which the client has to fill up.

You can send to customer this [pre-maid reply](/Templates/Emails).


