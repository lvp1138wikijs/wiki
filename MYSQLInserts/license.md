---
title:  Add / Remove Windows license costs 
description: 
published: true
date: 2021-03-26T11:32:56.290Z
tags: 
editor: markdown
dateCreated: 2021-03-26T11:32:56.290Z
---

#  Add / Remove Windows license costs 

## To remove windows license costs
> update cloudtrack set sc_freewindows = 1 where sc_username = "_username_";
> 
> INSERT INTO cloudtrack_vm_packages (sc_username,sc_vmid,sc_package,sc_price) SELECT sc_username,sc_vmid,replace(sc_package,"win-g","win-fg"),(sc_price - (sc_price * 2)) FROM cloudtrack_vm_packages WHERE sc_package like "win-%" and sc_username = "_username_";
{.is-info}

##  To add windows license cost back
> update cloudtrack set sc_freewindows = 0 where username = "_username_";
> DELETE from cloudtrack_vm_packages WHERE sc_package like "win-f%" and sc_username = "_username_";
{.is-info}
