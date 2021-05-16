---
title: HowTo block an IP traffic in windows
description: 
published: true
date: 2021-05-16T05:16:59.806Z
tags: 
editor: markdown
dateCreated: 2021-05-16T05:16:59.806Z
---

# To block an IP traffic follow these steps on your windows server:

Login to your windows server using RDP .
Then goto  the start  menu , then to administrative tools and then to  windows firewall with advanced security.
Next Click on the inbound rules option.
Next take the  New Rule section.
Next Click on the custom radio button and then click next.Select  All programs radio and click on the next button
Leave the  protocol and ports options as  default and click next.
Click on button  “these IP addresses ” and  Next  Click on the Add button.
we then  add the  IP address that we want to restrtict traffic to the rule
Then click on and then next
Make sure you select the Block the connection radio on the next screen and then click next.
Leave all of the options on the next screen checked
Now you are all set!