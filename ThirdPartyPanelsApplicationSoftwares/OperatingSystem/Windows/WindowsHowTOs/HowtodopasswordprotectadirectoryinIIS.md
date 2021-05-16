---
title: Howto do password protect a directory in IIS
description: 
published: true
date: 2021-05-16T05:52:04.154Z
tags: 
editor: markdown
dateCreated: 2021-05-16T05:52:04.154Z
---

- First connect to the website using the IIS manager.
 
- Next navigate to the directory that you wish to password protect.

- Next double click "Authorization Rules" 

- Click on Add deny rule and in teh pop up box select all the anonymous users

-  Finally click "ok" and the web.config file will be updated with password protection for that particular directory.