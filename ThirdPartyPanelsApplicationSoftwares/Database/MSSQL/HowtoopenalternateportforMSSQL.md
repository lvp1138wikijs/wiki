---
title: How to open alternate port for MSSQL
description: 
published: true
date: 2021-04-27T15:06:58.955Z
tags: 
editor: markdown
dateCreated: 2021-04-27T15:06:58.955Z
---

In order to open alternate port for MSSQL, please do the following steps:

1) Login to the server.

2) Go to SQL Server Configuration Manager (start->Microsoft SQL Server 2008 -> Configuration)

3) Open the "SQL network configuration" tab on the left.

4) Double click on the TCP/IP. section.

5) Click on the IP Addresses tab on the top

6) Go to bottom, the last field has 1433 in it, add a comma and add another number like 1536 and save.

7) Add 1536 as incoming and outgoing in Windows Firewall (Server manager -> Configuration -> Windows Firewall).

8) Restart SQL service.

