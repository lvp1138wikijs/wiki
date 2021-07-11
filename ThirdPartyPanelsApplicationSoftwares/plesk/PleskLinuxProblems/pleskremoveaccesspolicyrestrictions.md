---
title: plesk:remove access policy restrictions
description: 
published: true
date: 2021-07-11T00:27:30.219Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:27:30.219Z
---

# plesk:remove access policy restrictions

The access policy settings in plesk are sometimes set to deny connections from all IPs.

In this case we delete all the records from cp_access and replace the policy from "deny" to "allow"

Follow these steps:

```
mysql -uadmin -p`cat /etc/psa/.psa.shadow ` psa

 mysql> delete from cp_access;

mysql> update misc set val="allow" where param='access_policy';
```

Once you have changed the rule set you can login to the plesk panel from any IP address.

