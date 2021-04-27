---
title: Install SQL Server Web Edition in Server
description: 
published: true
date: 2021-04-27T16:37:27.198Z
tags: 
editor: markdown
dateCreated: 2021-04-27T16:37:27.198Z
---


> **The price for installing SQL Server Web Edition is $25.00/mo. Once customer approves the price and replies back with the server password, we can install it using the below steps**:
{.is-info}


1) Install Virtual-CloneDrive from Internet before proceeding to install SQL server.

(I used the link: http://download.cnet.com/Virtual-CloneDrive/3000-20432_4-173879.html )

2) Download the SQL webedition file from the IPMI access server 64.235.40.4 (C drive>>ISO)

Download this file to the server and Mount the file. After that, go to the Drive and Proceed with the setup. (Please refer the attached images for understanding each step of installing SQL Server Web Edition)

3) Once it is installed, make sure that the Sql port (1433) is enabled in the server firewall. If not, enable it in the server firewall and confirm if you can telnet fine to it.

 ----------------

1. To open a port in the Windows firewall for TCP access follow the below steps:

1. On the Start menu, click Run, type WF.msc, and then click OK.

1. In the Windows Firewall with Advanced Security, in the left pane, right-click Inbound Rules, and then click New Rule in the action pane.

1. In the Rule Type dialog box, select Port, and then click Next.

1. In the Protocol and Ports dialog box, select TCP. Select Specific local ports, and then type the port number of the instance of the Database Engine, such as 1433 for the default instance. Click Next.

1. In the Action dialog box, select Allow the connection, and then click Next.

1. In the Profile dialog box, select any profiles that describe the computer connection environment when you want to connect to the Database Engine, and then click Next.

1. In the Name dialog box, type a name and description for this rule, and then click Finish.

----------------



 