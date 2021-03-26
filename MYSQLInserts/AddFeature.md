---
title:  Add/Remove Features 
description: 
published: true
date: 2021-03-26T11:30:59.634Z
tags: 
editor: markdown
dateCreated: 2021-03-26T11:28:45.721Z
---

# Add/Remove Features (Shared accounts)

## Setup Extra FTP User for a Shared hosting account

> insert into extraaccounts (username,domain,directoryname,created,password,server,sc_username) values ("_FTP_username_","_domainname_","",1,"_password_",'_servername_','_main_username_');
{.is-info}


Example: FTP user: votevega, Domainname: vote.vegas, servername: maya.asdf456.com, password: tR5Li8jGtnm, main username: adlavac1
{.is-success}

insert into extraaccounts (username,domain,directoryname,created,password,server,sc_username) values ("votevega","vote.vegas","",1,"tR5Li8jGtnm",'maya.asdf456.com','adlavac1');





## Enable directory listing
> update sharedtrack_sites set sc_aindex=1 where sc_username='_USERNAME_' and sc_domain='_DOMAIN_NAME_';
{.is-info}



## Disable hotlink protection
> delete from userdata_preferences where feature = "refchk" and username = "username_here";
> insert into trigger (server,trigger,domain) select server,'webres',username from sharedtrack where username = "username_here";
{.is-info}



## Enable gzip compression
> insert into userdata_preferences (username,feature,value) values ("put_domainname_here","gz","1");
{.is-info}
