---
title: Tools to Check Plesk before Upgrade or Migration
description: 
published: true
date: 2021-12-16T17:44:50.275Z
tags: 
editor: markdown
dateCreated: 2021-12-16T17:44:50.275Z
---

# Tools to Check Plesk before Upgrade or Migration


Due to variations in the business model plan of Pleask Panel 10 most previous account settings are not portable from previous Plesk releases.

The below script can check whether the  accounts are suitable for migration or whether the Plesk Panel upgrade is possible:

> php plesk10_preupgrade_checker.php [plesk-admin-password] -d safe_mode=Off
{.is-info}


