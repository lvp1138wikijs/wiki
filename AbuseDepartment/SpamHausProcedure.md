---
title: SpamHaus Procedure
description: 
published: true
date: 2021-03-10T04:26:49.353Z
tags: 
editor: markdown
dateCreated: 2021-03-10T04:17:36.540Z
---

# SpamHaus Procedure

> If a server SUSPENDED due abuse, then keep the ticket OPEN and send an email to all staff.
{.is-warning}

**Procedure to handle SpamHaus Complaint**

Spamhaus complaints are extremely critical as their block usually affect the whole subnet. Assign them **TOP** priority.

SpamHaus reports always received to the gmail inbox folder. The subject should be **SBL Notify: IP: _IP_ADDRESS_ added to Spamhaus Block List (SBL)**. Below you can see an example email from SpamHaus

Once a complaint received to gmail account, then follow this procedure.

- First check the Server information from staff cp

### ***If its a new customer:*** 

- then definitely he is a spammer. Suspend server immediately and contact customer. Use  [this reply](/Templates/Spamhaustreplies).

1. Make sure RDNS not set on IPs. 
  a)Run command host xx.xxx.xxx.xx  (replace xx.xxx.xxx.xx with server ips). If its not set, then result should be lasvegas-nv-datacenter.com.
  b)If its set to a custom domain, then remove it from customer client portal.
  c)Login to client portal >> Click Server name >> Click on RDNS tab >> Remove the domain name related to IPs >>  Then save it.
   
1. Then contact spamhaus to delist IPs. Use this [Reply Template to contact spamhaus](/Templates/Spamhaustreplies)
1. Once all these procedure done, then contact Ms. Minerva with all details and also inform about the actions already done.

### ***If its an old customer***: 

- then inform customer about this. You can use the following [Reply Template for old cx](/Templates/Spamhaustreplies). May be some of their account hacked or any other issue. 
    - Wait for his reply. If he didn't reply on timely manner, then contact Ms. Minerva with all details and provide her a short history about customer. It will help to take a good decision.
   - History like how old he is, how many server he has, when he contacted us last time, how much he is paying, is there any older complaint from server, etc..
   
  
 A Sample Email From SpamHause ( reference only )
 
 ````
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



