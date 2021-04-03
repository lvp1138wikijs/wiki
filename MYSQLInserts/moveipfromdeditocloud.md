---
title: Queries to move an IP from Dedicated to colossuscloud 
description: 
published: true
date: 2021-04-03T09:52:44.796Z
tags: 
editor: markdown
dateCreated: 2021-04-03T09:52:44.796Z
---

# Header
-     These are some queries to move IPs from a Dedicated  to a colossuscloud one. This will NOT WORK in every case.
-     These queries require the VMID of the colossuscloud VM. Get it from the new admin panel.

> update iplist_vps set sc_vmid = '',sc_username = '',sc_hv = '' where sc_type = 'pub' and sc_vmid = '_VMID_';
>  
> INSERT INTO iplist_vps (sc_vmid,sc_username,sc_ipnumber,sc_classc,sc_lastoct,sc_netmask,sc_gateway,sc_vlan,sc_zone,sc_type) VALUES ('_VMID_','_username_','_IP1_','_c-class_','_last-oct-IP1_','_netmask_','_gateway_','_vlan_','_cloud-zone_','pub');
> INSERT INTO iplist_vps (sc_vmid,sc_username,sc_ipnumber,sc_classc,sc_lastoct,sc_netmask,sc_gateway,sc_vlan,sc_zone,sc_type) VALUES ('_VMID_','_username_','_IP2_','_c-class_','_last-oct-IP2_','_netmask_','_gateway_','_vlan_','_cloud-zone_','pub');
>  
> delete from cidrtracker where sc_vmid = '_VMID_';
> delete from cidrtracker where username = '_username_' and sc_vmid = '_VMID_';
>  
> insert into cidrtracker (hostname,classc,iprange1,iprange2,username,service,sc_vmid) values ('_hostname_','_c-class_','_last-oct-IP1_','_last-oct-IP1_','_username_','cplus','_VMID_');
> insert into cidrtracker (hostname,classc,iprange1,iprange2,username,service,sc_vmid) values ('_hostname_','_c-class_','_last-oct-IP2_','_last-oct-IP2_','_username_','cplus','_VMID_');
>  
> update cloudtrack_vm set sc_hostname = '_hostname_' where sc_vmident = '_VMID_';
>  
> #this will delete ALL reverse DNS entries of the VM under username
> delete from dns_reverse where sc_vmid = '_VMID_';
> delete from dns_reverse WHERE username = '_username_' and sc_vmid = '_VMID_';
>   
> #Update IP limits
> UPDATE cloudtrack_vm_resources SET sc_value = "_total_number_of_ips_minus_one_" WHERE sc_vmid = "_VMID_" AND sc_feature = "ip";
>  
> #Delete IP address from Dedicated Interface Table
> delete from iplist_dedi where sc_ipnumber = "_IP1_";
> delete from iplist_dedi where sc_ipnumber = "_IP2_"
{.is-info}


Replace following values :-
> _VMID_
> _IP2_
> _IP1_
> _username_
> _c-class_
> _last-oct-IP1_
> _last-oct-IP2_
> _netmask_
> _gateway_
> _vlan_
> _cloud-zone_
> _hostname_
> _total_number_of_ips_minus_one_ : Basically, if a VM has 8 IPs, that value there should be 7 (because one IP is free).
> 

Sample:-
> update iplist_vps set sc_vmid = '',sc_username = '',sc_hv = '' where sc_type = 'pub' and sc_vmid = '3230457a0bd268f3691ad4757b24ff8c';
>  
> INSERT INTO iplist_vps (sc_vmid,sc_username,sc_ipnumber,sc_classc,sc_lastoct,sc_netmask,sc_gateway,sc_vlan,sc_zone,sc_type)
> VALUES ('3230457a0bd268f3691ad4757b24ff8c','lvp1138','72.18.207.148','72.18.207','148','255.255.255.128','72.18.207.129','207','las1-1','pub');
>  
> delete from cidrtracker where sc_vmid = '3230457a0bd268f3691ad4757b24ff8c';
> delete from cidrtracker where username = 'lvp1138' and sc_vmid = '3230457a0bd268f3691ad4757b24ff8c';
>  
> insert into cidrtracker (hostname,classc,iprange1,iprange2,username,service,sc_vmid)
> values ('72-18-207-148','72.18.207','148','148','lvp1138','cplus','3230457a0bd268f3691ad4757b24ff8c');
>  
> update cloudtrack_vm set sc_hostname = '72-18-207-148' where sc_vmident = '3230457a0bd268f3691ad4757b24ff8c';
>  
> #this will delete ALL reverse DNS entries of the VM under username
> delete from dns_reverse where sc_vmid = '3230457a0bd268f3691ad4757b24ff8c';
> delete from dns_reverse WHERE username = 'lvp1138' and sc_vmid = '3230457a0bd268f3691ad4757b24ff8c';
>   
> #Update IP limits
> UPDATE cloudtrack_vm_resources SET sc_value = "0" WHERE sc_vmid = "3230457a0bd268f3691ad4757b24ff8c" AND sc_feature = "ip";
>  
> #Delete IP address from Dedicated Interface Table
> delete from iplist_dedi where sc_ipnumber = "72.18.207.148"; 
{.is-info}

## If VM is Cpanel based
> update cpanel_licenses set sc_ipnumber = "_old_VM_cpanel_Licenses_IP_", sc_licenseid = "_old_VM_cpanel_Licenses_ID_"  where sc_serverid = "_VMID_";
{.is-info}

> - *cidrtracker* To retrieve license ip, open this url while you are login to Cpanel licensing interface
> http://manage2.cpanel.net/XMLlookup.cgi?ip=64.235.39.106
> - replace IP with your VM ip



##  Queries to Move IPs between ColossusCloud Vms

> #First step: remove all extra IPs from the old VM. You can do that from client portal.
>  
> #Second: with this query, we remove the IPs of the NEW VM:
> update iplist_vps set sc_vmid = '',sc_username = '',sc_hv = '' where sc_type = 'pub' and sc_vmid = '<new_vm_id>';
>  
> #Delete the IPs from the source VM:
> DELETE FROM iplist_vps WHERE sc_ipnumber = '<ip_to_be_moved>';
>  
> #Let's reinsert them again with the NEW vimd:
> INSERT INTO iplist_vps (sc_vmid,sc_username,sc_ipnumber,sc_classc,sc_lastoct,sc_netmask,sc_gateway,sc_vlan,sc_zone,sc_type) VALUES ('<new_vm_id>','<username>','<IP>','<classc>','<lastoct>','<netmask>','<gateway>','<vlan>','<zone>','<type>');
>  
> #Delete IPs from old table of OLD VMID
> delete from cidrtracker where username = '<username>' and sc_vmid = '<old_vm_id>';
>   
> #Delete IPs from old table of NEW VMID
> delete from cidrtracker where username = '<username>' and sc_vmid = '<new_vm_id>';
>  
> #lets reinsert IPs into new table with the NEW VMID
> insert into cidrtracker (hostname,classc,iprange1,iprange2,username,service,sc_vmid) values ('new-vm-ip-address','<classc>','_ip1_','_ip1_','<username>','cplus','<new_vm_id>');
>   
> #and this is fine. Use primary IP as sc_hostname
> update cloudtrack_vm set sc_hostname = 'new-vm-ip-address' where sc_vmident = '<new_vm_id>';
> 
> 
{.is-info}

  
**  Example : IP - 216.108.231.35  move to  VM 08d1c8ee9e1e361d2166834502b9cbbe from old VM ID : 1be3ecd37dea03f3ac01b04472e4dc3a**
  
>   #First step: Remove all extra IPs from the old VM. You can do that from client portal.
>  
> #Second: with this query, we remove the IPs of the NEW VM:
> update iplist_vps set sc_vmid = '',sc_username = '',sc_hv = '' where sc_type = 'pub' and sc_vmid = '08d1c8ee9e1e361d2166834502b9cbbe';
>  
> #Delete the IPs from the source VM:
> DELETE FROM iplist_vps WHERE sc_ipnumber = '216.108.231.35';
>  
> #Let's reinsert them again with the NEW vimd:
> INSERT INTO iplist_vps (sc_vmid,sc_username,sc_ipnumber,sc_classc,sc_lastoct,sc_netmask,sc_gateway,sc_vlan,sc_zone,sc_type) VALUES ('08d1c8ee9e1e361d2166834502b9cbbe','wmifabri','216.108.231.35','216.108.231','35','255.255.255.0','216.108.231.1','231','scl1-1','pub');
>  
> #Delete IPs from old table of OLD VMID
> delete from cidrtracker where username = 'wmifabri' and sc_vmid = '1be3ecd37dea03f3ac01b04472e4dc3a';
>  
> #Delete IPs from old table of NEW VMID
> delete from cidrtracker where username = 'wmifabri' and sc_vmid = '08d1c8ee9e1e361d2166834502b9cbbe';
>  
> #lets reinsert IPs into new table with the NEW VMID
> insert into cidrtracker (hostname,classc,iprange1,iprange2,username,service,sc_vmid) values ('216-108-231-35','216.108.231','35','35','wmifabri','cplus','08d1c8ee9e1e361d2166834502b9cbbe');
>   
> #and this is fine. Use primary IP as sc_hostname
> update cloudtrack_vm set sc_hostname = '216-108-231-35' where sc_vmident = '08d1c8ee9e1e361d2166834502b9cbbe';
>   
{.is-info}

  
  
  
  
  

*We have to also add below query other wise the IP address usage will not be updated and we can see a spinning icon in the IP tab.

> UPDATE cloudtrack_vm_resources SET sc_value = "_total_number_of_ips_minus_one" WHERE sc_vmid = "_vmid_" AND sc_feature = "ip";*
{.is-success}

