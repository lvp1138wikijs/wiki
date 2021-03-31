---
title: Suspend / Un-suspend
description: 
published: true
date: 2021-03-31T00:06:19.716Z
tags: 
editor: markdown
dateCreated: 2021-03-30T23:56:38.114Z
---


> NOTE
> 
> 1. Billing system try to charge an account after every other day from its next payment date (NPD), after that it suspend account (shared hosting) or send suspension notice to ticket system (dedicated servers/VPS/Cloud+).
> 1. Dedication Servers/VPS/Cloud+ are suppose to suspend due to non payment, only after you receive message from system in ticket, otherwise system will not try to automatically reactivate when client will make payment, and no notice will arrive in ticket system and customer will complain about non reactivation upon his payment.
{.is-info}

> **CANCELLATION AFTER SUSPENSION**
> 
> - We suspend a suspicious server and keep suspended for at least 15 days and even the entire month if we dont need to rent that server right away.
> - With VPS we can keep suspended for an entire month before cancelling. That is to protect us in case it a real account and they have data on it.
{.is-success}

> **IMPORTANT**
> 
> It is important then when you suspend a server due to policy violation issue, then send a note to all the staff so that they are aware of suspension. In case customer contact using different email address then staff on duty do not waste time in finding that why server is not responding.
{.is-warning}


**Suspend /Un-suspend Procedures for Shared/Dedicated/VPS hosting account**

**Reasons for Suspension**

- **Payment issue**: Our system will automatically suspend due **shared** accounts after a particular time period. For Dedicated / VPS accounts system will send notification to ticketing system. We need to suspend it manually. 
- 
- **Charge back**: Accounts will be suspended immediately if  any customer place a charge back on their payment. We need to suspend manually. If its an old customer, then confirm with Minerva before suspending account.
- 
- **Abuse issue**: Issues like spam, phishing, copyright, etc... If its an old customer, then confirm with Minerva before suspending account. Also collect all possible details about that customer

**Shared Account**

**Suspension due to non payment**

System suspend non paid account automatically after 10 days of next payment date (NPD). There is no manual action required for this from customer support department.

**Un-Suspension after payment**

System automatically un-suspend account, once payment is done. Therefore If a customer contact, then tell him to [make payment from control panel](/AccountingProcedure/AccountingProcedure/Billing) and account will be automatically reactivated and a notification email will arrive in tickets like below.

```
Subject: 425867; REACTIVATED: personalityboxes.com

This account has been automatically reactivated. Invoice is now paid. Please confirm.
Domain: personalityboxes.com
Invoice number: 425867
This notice is ONLY sent when a previously suspended account is reactivated.
```

**Suspension due to charge back/Abuse issue**

Below mentioned manual procedure require to adopt in case of this suspension.

**Procedure to suspend  account manually**

This manual procedure is only need for suspend account due to charge back and abuse issues. System will automatically suspend/unsuspend  account due to billing issues.

To suspend a shared account. Please send the insert to Ms. Minerva. 

**Dedicated Service**

**Due to non payment**

To suspend a server for lack of payment when you get the suspension notice (sample below) from our billing software, just Turn OFF the server's Ethernet port.  This can be done from staff cp (Search SN>> CLick Hostname>> Change 1G to Disable)

**Suspension notification for Dedicated Server**

```
Subject: 422340; TO SUSPEND: httpsoun-64-235-53-82.serverpoint.com

Please suspend service to this client. Do so only between 9AM and 12PM PST, Monday through Thursday.
Invoice number: 422340
Amount due: 143.99
Due date: 2012-09-30
This notice is ONLY sent on the 6th attempt to charge client, whether to charge their credit card or from credit.
```

Do not suspend servers on weekends due to payment issue. Preferably do this on from Monday - Thursday


When a client pays his/her invoice, whether it is via the client portal or because we have updated a new credit card, etc, the system will automatically reactivate server by enabling its Ethernet port, and will send a notice to ticket system (sample below). All you need is to check and confirm that server is up.

**Re-activation notification for Dedicated server**
 
```
Subject: 382059; SUSPENDED S/N 1562 now reactivated: check!
To: system-alerts@serverpoint.com


Server 1562 had its ethernet port disabled due to suspension, but now has been automatically enabled. Confirm.
```

**Due to Abuse / ChargeBack / Others**

To suspend just disable Ethernet port from staff cp (Search SN>> CLick Hostname>> Change 1G to Disable)

To activate just Enable Ethernet port (Search SN>> CLick Hostname>> Change DISABLE to 1 G port)

**VPS Service**

For payment issues, system will send a suspend notification to ticketing system. We need to suspend those servers manually.

**For suspension notification will be**

```
Subject: 423628; SUSPEND CLOUD SERVICE FOR USER: jamieswa

Please suspend service to this client. Do so only between 9AM and 12PM PST, Monday through Thursday.
Invoice number: 423628
Amount due: 20.99
Due date: 2012-10-04
This notice is ONLY sent on the 6th attempt to charge client, whether to charge their credit card or from credit.
```

**For un-suspension notification will be**

```
Subject: 427067; REACTIVATE CLOUD FOR USER: sharprac

Please reactivate cloud service to client sharprac. Invoice has been paid.
Invoice number: 427067
This notice is ONLY sent when a previously suspended account is reactivated.
```

**Suspend Colossus VPS Service**

 To suspend a colossus vps you can follow the steps given below

1) Search the username and click edit
2) From there you can suspend the VPS account due to fraud or payment. 
