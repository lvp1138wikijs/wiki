---
title: How to Add/Remove IP blocks using Plesk
description: 
published: true
date: 2021-07-11T01:17:51.267Z
tags: 
editor: markdown
dateCreated: 2021-07-11T01:17:51.267Z
---

Reference Ticket: NCZ-611-65684.

If a Plesk customer wants to add an IP to his block list of remove an IP from his block list follow these steps. It will work only if plesk firewall feature enabled.

**To add an IP to block list**

```
Login to Plesk >> Settings >> Manage Firewall Rules [under 'Security'] >> Edit Firewall Configuration >> Add Custom Rule >> enter the following details.

Name of the rule – Block
Match direction - Incoming
Action – Deny
Sources – the IP address you want to block

Click “OK” >> click “Activate”.
```

**To remove IP from block list** 

```
Login to Plesk >> Settings >> Manage Firewall Rules [under 'Security'] >> Edit Firewall Configuration >> Add Custom Rule >> enter the following details.

Name of the rule – Block
Match direction - Incoming
Action – Allow
Sources – the IP address you want to block

Click “OK” >> click “Activate”.
```



