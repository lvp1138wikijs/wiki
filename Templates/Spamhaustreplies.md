---
title: Spamhaus Reply Templates and Emails
description: 
published: true
date: 2021-03-10T04:04:34.071Z
tags: 
editor: markdown
dateCreated: 2021-03-10T04:04:34.071Z
---

**Reply Template for New Customer**

```

Hello,

This is ........ from ServerPoint. I hope you are doing good.

We recently noticed that your IPs are added in spamhaus. You can see the detail from following url

-------------
Url in SpamHaus Complaint
-------------

What kind of service you are running on the server and why its getting listed ?.
Right now your server suspended due to our vilation policy. Please contact us asap and let us know for what purpose this server is being used.

Regards,

````

**Reply Template for OLD customer**

```
Hello,

This is ........ from ServerPoint. I hope you are doing good.

We recently noticed that your IPs are added in spamhaus. You can see the detail from following url

-------------
Url in SpamHaus Complaint
-------------

Please take immediate appropriate actions to avoid service interruption and let us know for what purpose this server is being used.

If we don't hear from you within then next 24 hours, your server may be suspended due to violation to our policies.

Regards,
```

**A Sample Email From SpamHause ( reference only )**

```
------------------------------------------------------------------------
SBL124102 - The Spamhaus Project - SBL International Anti-Spam System
------------------------------------------------------------------------

Hello serverpoint.com Abuse Desk,

This is an automated message from the Spamhaus Block List (SBL) database
to advise you that the IP below has been added to sbl.spamhaus.org:

IP/cidr: 64.235.57.119/32

Problem: spam emitter

SBL Ref: SBL124102

The reason for listing the IP address(es) is explained at the url:
http://www.spamhaus.org/sbl/sbl.lasso?query=SBL124102

If you have already taken care of this problem and the spammer is no
longer operating any domains/sites/servers in 64.235.57.119/32 you
can send a removal request for record SBL124102 by emailing:
<mailto:sbl-removals@spamhaus.org?subject=SBL124102_64.235.57.119/32_SR03>

Note that your email must tell us how the spam problem has been terminated
(we need to know exactly how the issue has been dealt with and that this
spam problem is fully terminated)

Please always include "SBL124102 SR03" in the Subject of any emails to
sbl-removals@spamhaus.org regarding this listing.

SBL System Robot
The Spamhaus Project
http://www.spamhaus.org

------------------------------------------------------------------------
You can review all current SBL listings concerning your network here:
http://www.spamhaus.org/sbl/listings.lasso?isp=serverpoint.com
------------------------------------------------------------------------
You are receiving this notification because you are the designated abuse
contact for your network. If you do not want to be alerted whenever IPs
on your network are listed in the SBL, please advise us by contacting
<mailto:sbl-autonotify@spamhaus.org?subject=STOP_Notify_serverpoint.com>
------------------------------------------------------------------------
ISP Abuse Desk Resources.....: http://www.spamhaus.org/isp
Spamhaus Block List (SBL)....: http://www.spamhaus.org/sbl
Exploits Block List (XBL)....: http://www.spamhaus.org/xbl
Register Of Known Spammers...: http://www.spamhaus.org/rokso
------------------------------------------------------------------------
```

**Reply Template to Contact SpamHaus Team**

SpamHaus Email address: **sbl-removals@spamhaus.org**

It is essential that emails to the SBL Team about on SBL listing include exact ticket information in the email Subject. You can find it from SpamHaus reason url.

For example, In the above complaint the email subject was **SBL124102_64.235.57.119/32_SR03** 

```
Hello,

This is ........ from ServerPoint.

The offending server has been now removed. Please remove the listing.

Thank you.
```
