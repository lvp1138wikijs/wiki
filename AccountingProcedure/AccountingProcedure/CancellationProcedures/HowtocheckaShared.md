---
title: How to check a Shared/Dedicated/VPS Account is Active or Cancelled
description: 
published: true
date: 2021-03-24T06:00:29.767Z
tags: 
editor: markdown
dateCreated: 2021-03-24T06:00:29.767Z
---

**Shared**:

- Login to Old ICP. 
- If a main/resold account active then it should be list in Shared - Active.
- If they are cancelled then should be list in Shared - Cancel

**Dedicated**:

- Login to Old ICP > Then click on Search dedi/colo Assign/Deassign > then search with ipaddress or the username
- If its cancelled then output will be unassigned-64-235-40-16.serverpoint.com 
- If its active, then output will be username-IP_address.serverpoint.com

**VPS**

- Login to Old ICP > Then click on Search dedi/colo Assign/Deassign > then search with ipaddress or the username.
- If its cancelled then didn't get any output. That means the VPS is cancelled / do not exist.
- If its active, then result will be like following.
   - For Virtuozzo VPS: 
       - ICP output will be like vps-vz1-vpsw2k3complete-216-108-226-16.serverpoint.com
     - Also Login to PIM/PVA to confirm if its active or not
   - For Cloud VM:  
      - ICP output will be like  cloud-las1-user-IP / Cloud VPS account
      - Also login to Onapp to confirm if its active or not
      
      