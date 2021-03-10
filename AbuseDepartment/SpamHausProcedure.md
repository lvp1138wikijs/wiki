---
title: SpamHaus Procedure
description: 
published: true
date: 2021-03-10T04:19:44.247Z
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
   
  

