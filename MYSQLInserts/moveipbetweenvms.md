---
title:  Query to move IP between colossuscloud VMs 
description: 
published: true
date: 2021-04-03T10:53:32.166Z
tags: 
editor: markdown
dateCreated: 2021-04-03T10:53:32.166Z
---


> update iplist_vps set sc_vmid = "<destinationvmid>",sc_hv = "<hv>",sc_dateassigned = current_timestamp() where sc_ipnumber = "<iptomove>";
{.is-info}
  
  
  Eg: - If you want to move an IP "64.235.37.192" from source VM to destination VM "646f132e0a59e121beb66fa36b82c482", the query should be as follows :
  
>   update iplist_vps set sc_vmid = "646f132e0a59e121beb66fa36b82c482",sc_hv = "ams1-1-1",sc_dateassigned = current_timestamp() where sc_ipnumber = "64.235.37.192";
{.is-info}
  
  The above query is to only assign the new IP to the vm. You have to delete the old IP from the destination VM. The old IP of the destination VM can be removed from the client portal.
Settings>>Info/Ips>> Delete the IP

