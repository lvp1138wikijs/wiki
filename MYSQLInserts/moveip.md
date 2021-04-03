---
title: Move IP address from Old Table to New Table 
description: 
published: true
date: 2021-04-03T09:44:07.212Z
tags: 
editor: markdown
dateCreated: 2021-04-03T09:44:07.212Z
---

Example: Move IP  64.235.36.104 to new table.

> INSERT INTO iplist_dedi (sc_zone,sc_ipnumber,sc_classc,sc_lastoct,sc_netmask,sc_gateway,sc_vlan) VALUES ('las1-1','64.235.36.104','64.235.36','104','255.255.255.0','64.235.36.1','36');
{.is-info}
