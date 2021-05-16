---
title: How to Allow an IP or IP Range Using Windows IP Security Policy
description: 
published: true
date: 2021-05-16T05:13:30.403Z
tags: 
editor: markdown
dateCreated: 2021-05-16T05:13:30.403Z
---

## Setting up the IP Policy

```
Log into your dedicated server using Remote Desktop.
Click Start > Run >type MMC press OK.
In the console click File > Add/Remove Snap in.
Select the IP Security Policy Managment item in the Available snap-ins list click the Add button.
Leave Local Computer checked and click Finish and then OK. You should now be back to the console.
If no Security Policy exists yet, in the Left frame right click IP Security Policies on Local Computer and then click Create IP Security Policy then continue to next step.  If a Security Policy does exist, right click on it in the Right pane and click Properties then continue to next section (Setting up the IP Filters)
Click Next on the first page of the Wizard
Name your IP Security Policy and provide a description if desired, then click Next.
Check the box for the Activate the default response rule option then click Next.
Leave the Active Directory default option on the Default Response Rule Authentication Method page selected and click Next.
On the final page of the Wizard leave the Edit properties option checked and click Finish. You should now have the properties window open.
```

## Setting up the IP Filters to ALLOW access


```
Click Add then click Next to continue.
Leave This rule does not specify a tunnel selected and click Next.
Leave all network connections selected and click Next.
You should now be on the IP filter list. You need to create a new filter, so don't select any of the default ones. Click Add.
Type a Name for your list, and a Description if desired.
Leave Mirrored. Match packets with the exact opposite source and destination addresses checked. Click Next.
Select A specific IP Address of Subnet as the Source address, enter the IP of Subnet you want to allow (see note above for PowerDNN subnets) then click Next.
You can now select A Specific IP Address or Any IP Address for the Destination address.
Select the Protocol Type you wish to allow access to. Click Next and then Finish.
Complete the steps above for each additional IP address you want to add to the Filter.
Once you have added all the required IP Addresses to the list click OK.
Select the list you have just created from the IP Filter List and click Next.
In the Filter Action box click Add to create a new Action for the List you've selected.
Click Next on the first page of the Filter Action Wizard
Give your action a name such as AllowConnection and click Next.
Select the Permit radio button and click Next.
Click Finish.
Select the Filter Action you've just created and click Next then Finish.
Click OK to close the RDP Policy Properties box.
```