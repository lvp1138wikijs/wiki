---
title: MySql Inserts
description: Queries
published: true
date: 2021-03-03T10:28:03.861Z
tags: mysql, inserts
editor: markdown
dateCreated: 2021-03-03T10:28:03.861Z
---

# Header
Add/Remove Features


**Change A Record of Main Website**
`
delete from dns_settings where entry_type = "A" and entry_value1 = "" and domain = "Main_domain";
insert into dns_settings (domain,entry_type,entry_value1,entry_value2,tocreate) values ("Main_domain","A","","IP_Address",1); 

`

Create A Record for Sub domain

`
delete from dns_settings where entry_type = "A" and entry_value1 = "Sub_value" and domain = "Main_domain";
insert into dns_settings (domain,entry_type,entry_value1,entry_value2,tocreate) values ("Main_domain","A","Sub_value","IP_Address",1);
`
> note : Replace Sub_value, Main_domain with correct details

Example : Add 'A' record for subdomain account.hiimwildfire.com to the IP 174.120.50.58

`
delete from dns_settings where entry_type = "A" and entry_value1 = "account" and domain = "hiimwildfire.com";
insert into dns_settings (domain,entry_type,entry_value1,entry_value2,tocreate) values ("hiimwildfire.com","A","account","174.120.50.58",1);
`
