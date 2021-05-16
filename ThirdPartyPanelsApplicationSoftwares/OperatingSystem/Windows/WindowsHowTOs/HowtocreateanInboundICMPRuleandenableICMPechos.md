---
title: How to create an Inbound ICMP Rule and enable ICMP echos?
description: 
published: true
date: 2021-05-16T05:25:24.674Z
tags: 
editor: markdown
dateCreated: 2021-05-16T05:25:24.674Z
---

# How to create an Inbound ICMP Rule and enable ICMP echos?

An Echo is simply what most people call a 'ping'. The Echo Reply is the 'ping reply'. ICMP (Internet Control Message Protocol) Echos are used mostly for troubleshooting.When there are 2 hosts which have communication problems, a few simple ICMP Echo requests will show if the 2 hosts have their TCP/IP stacks configured correctly and if there are any problems with the routes packets are taking in order to get to the other side.

 
**To enable ICMP replies in Windows Server 2008 you must allow ICMP packets through the windows Firewall, you can do that using the following steps**.

- Press **Start**
- Goto -> **Administrative tools**
- Click on '**Windows Firewall with Advanced Security**'
- Click on '**Inbound Rules**'
- Scroll down to find: '**File and Printer Sharing** (Echo Request - ICMPv4-In)'
- Right-click on this and choose '**Enable Rule**'

Once you enable the rule you can now ping the windows 2008 server.

It is the responsibility of the network layer (IP) protocol to ensure that the ICMP message is sent to the correct destination. This is achieved by setting the destination address of the IP packet carrying the ICMP message. To allow inbound Internet Control Message Protocol (ICMP) network traffic, use the Windows Firewall with Advanced Security node in the Group Policy Management MMC snap-in to create firewall rules.This type of rule allows ICMP requests and responses to be sent and received by computers on the network.

**To create a inbound in ICMP rule, follow the steps given below**

- Open the Group Policy Management Console to Windows Firewall with Advanced Security
- In the navigation pane, click Inbound Rules.
- Click Action, and then click New rule. 
- On the Rule Type page of the New Inbound Rule Wizard, click Custom, and then click Next. 
- On the Program page, click All programs, and then click Next.
- On the Protocol and Ports page, select ICMPv4 or ICMPv6 from the Protocol type list. If you use both IPv4 and IPv6 on your network, you must create a separate ICMP rule for each. 
- Click Customize.  
- In the Customize ICMP Settings dialog box, do one of the following:
   - To allow all ICMP network traffic, click All ICMP types, and then click OK.
   - To select one of the predefined ICMP types, click Specific ICMP types, and then select each type in the list that you want to allow. Click OK
   - To select an ICMP type that does not appear in the list, click Specific ICMP types, select the Type number from the list, select the Code number from the list, click Add, and then select the newly created entry from the list. Click OK
- Click Next.
- On the Scope page, you can specify that the rule applies only to network traffic to or from the IP addresses entered on this page. Configure as appropriate for your design, and then click Next.
- On the Action page, select Allow the connection, and then click Next.
- On the Profile page, select the network location types to which this rule applies, and then click Next.
- On the Name page, type a name and description for your rule, and then click Finish.