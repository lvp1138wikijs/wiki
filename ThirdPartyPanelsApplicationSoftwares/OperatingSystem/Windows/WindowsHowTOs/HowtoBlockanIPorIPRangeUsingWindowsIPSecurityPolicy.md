---
title: How to Block an IP or IP Range Using Windows IP Security Policy
description: 
published: true
date: 2021-05-16T05:15:55.692Z
tags: 
editor: markdown
dateCreated: 2021-05-16T05:15:55.692Z
---

## Setting up the IP Policy

```
Log into your dedicated server using Remote Desktop.
Click Start > Run >type MMC press OK.
In the console click File > Add/Remove Snap in.
Select the IP Security Policy Managmentitem in theAvailable snap-ins list click the Add button.
LeaveLocal Computer checked and click Finish and then OK. You should now be back to the console.
If no Security Policy exists yet, in the Left frame right click IP Security Policies on Local Computerand then clickCreate IP Security Policy then continue to next step.  If a Security Policy does exist, right click on it in the Right pane and click Properties then continue to next section (Setting up the IP Filters)
Click Next on the first page of the Wizard
Name your IP Security Policy and provide a description if desired, then click Next.
Check the box for the Activate the default response rule option then click Next.
Leave the Active Directory default option on the Default Response Rule Authentication Method page selected and click Next.
On the final page of the Wizard leave the Edit properties option checked and click Finish. You should now have the properties window open.
```

## Setting up the IP Filters to BLOCK access

Using Any IP Address as the IP Traffic Source will block access from all sources and is not recommended unless blocking access to a single protocol such as RDP,
you will first need to complete the steps above to allow access to the PowerDNN subnet, and any other IP addresses you wish to allow access to your server.

```
Click Add then click Next to continue.
Leave This rule does not specify a tunnel selected and click Next.
Leave all network connections selected and click Next.
You should now be on the IP filter list. You need to create a new filter, so don't select any of the default ones. ClickAdd.
Type a Name for your list, and a Description if desired.
Click Add... then click Next to continue.
In the description box type a description.
Leave Mirrored. Match packets with the exact opposite source and destination addresses checked. ClickNext.
Select the Source of the traffic you with to block then click Next. 
You can now select A Specific IP Address or Any IP Address for the Destination address.
If you have selected A specific IP Address, type in the IP Address you want to block. Click Next.
Select the Protocol Type you wish to block, or select Any if you want to block access to all protocols. Next and then Finish.
Complete the steps above for each additional IP address you want to add to the Filter list, or if you have blocked all IP addresses continue to the next step.
Once you have added all the required IP Addresses to the list click OK.
Select the list you have just created from the IP Filter List and click Next.
In the Filter Action box select the BlockConnection option and click Next.
Click Finish.
Click OK to close the RDP Policy Properties box.
Once you're back in the Console/IP Security Policies screen, right click on the Policy you have just created and select Assign. This step will not be necessary if you are using an existing Policy.

```

