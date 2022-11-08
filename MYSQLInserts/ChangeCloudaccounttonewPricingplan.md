---
title:  Change Cloud account to new Pricing plan 
description: 
published: true
date: 2022-11-08T17:49:56.455Z
tags: 
editor: markdown
dateCreated: 2021-03-26T12:07:40.347Z
---


Use the below inserts to change the Slider plan VPS (with old pricing plan) to new Size-based Plan



> update cloudtrack set sc_disc = '0' where sc_username = '_username_';
> 
> delete from userdata_preferences where feature = 'vpsmode' AND username = '_username_';
> 
> insert into userdata_preferences (username,feature,value) values ('_username_','vpsmode',1);
{.is-info}



Change '_username_' with CP username.