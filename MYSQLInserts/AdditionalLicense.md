---
title:  CCloud Additional License
description: 
published: true
date: 2021-03-26T12:04:57.256Z
tags: 
editor: markdown
dateCreated: 2021-03-26T12:04:57.256Z
---

#  CCloud Additional License 
Whenever a customer is adding  an additional license  ( CAL license, Plesk or SQL) to their VM, below query needs to be executed :
## Query to add license :
> insert into cloudtrack_vm_packages (sc_username,sc_vmid,sc_package,sc_price) select "<username>","vm_id>",sc_feature,sc_value from cloudtrack_pricingplans where sc_feature = "<product_code>";
{.is-info}

  
  **Eg:-**
  insert into cloudtrack_vm_packages (sc_username,sc_vmid,sc_package,sc_price) select "hookyour","3df4b73c0dca3ff28d6bcfa44cbc0d50",sc_feature,sc_value from cloudtrack_pricingplans where sc_feature = "ms5cal";
  
###   Product codes:
> | plesk10      | 12.00       
> 
> | plesk30      | 29.00      
> 
> | plesku        | 59.00       
> 
> | ms5cal      | 10.00       
> 
> | mssqlweb     | 25.00       
> 
> | mssqlwrkg    | 65.00       
> 
> | mssqlstd      | 249.00      
> 
> | mssqlent     | 949.00      
> 
> | msofficestd   | 15.00       
> 
> | msofficepro  | 19.00    
>   
{.is-success}
  
##   Query to remove an additional license:
  Here is the query to remove an additional license from customer account
>   delete from cloudtrack_vm_packages where sc_username = "<username>" and sc_package = "product_code";
{.is-info}

Eg:-
  delete from cloudtrack_vm_packages where sc_username = "mohamedi" and sc_package = "mssqlweb";
  
##   Query to remove an additional license for a VM:
>   delete from cloudtrack_vm_packages where sc_username = "_username_" and sc_vmid = "_vmid_" and sc_package = "_feature_";
{.is-info}
