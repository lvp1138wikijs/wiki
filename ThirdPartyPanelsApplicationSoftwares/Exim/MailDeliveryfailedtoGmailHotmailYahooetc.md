---
title: Mail Delivery failed to Gmail, Hotmail, Yahoo etc
description: 
published: true
date: 2021-07-25T03:48:15.491Z
tags: 
editor: markdown
dateCreated: 2021-07-25T03:48:15.491Z
---

# Mail Delivery failed to Gmail, Hotmail, Yahoo etc

Customer reports that the mails sent to Gmail, Hotmail, Yahoo or other domains are getting rejected with similar bounce back messages, as given below:


```
A message that you sent could not be delivered to one or more of its recipients. This is a permanent error. The following address(es) failed:
 sserverpoint@gmail.com
 SMTP error from remote mail server after end of data: host gmail-smtp-in.l.google.com [74.125.25.27]: 550-5.7.1 [64.235.48.216 12] Our system has detected that this message is 550-5.7.1 likely unsolicited mail. To reduce the amount of spam sent to Gmail,
 550-5.7.1 this message has been blocked. Please visit 550-5.7.1 http://support.google.com/mail/bin/answer.py?hl=en&answer=188131 for 550 5.7.1 more information. tx1si74564pbc.150 - gsmtp
```

**SOLUTION**:

```
1) First ensure that the IP address of mail server is not blacklisted.
2) Check mail queue and ensure that no spamming is happening from the server. 
3) Then change the mail interface IP, if the server has more than one IP address assigned to it.
/etc/mailips - This file specifies from which IP addresses mail should be sent.
4) In cpanel servers, in order to specify which IP address should handle outbound mail, you will need to properly set the following options in WHM's Exim Configuration Manager.
"Reference /etc/mailips for outgoing SMTP connections"
5) Then edit the file /etc/mailips. The entry looks like,
*: IP
6) Save the file and restart exim.
```

**Mail delivery will work fine**.
