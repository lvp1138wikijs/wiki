---
title: WHM Configuration
description: 
published: true
date: 2022-01-06T06:27:16.593Z
tags: 
editor: markdown
dateCreated: 2022-01-06T06:27:16.593Z
---

# WHM Configuration

Login to the WHM by typing https://yourip:2087   , with ‘ root ‘ as username and with the password.

The Initial Setup screen shown now is with steps 1 to 6.

**STEP 1**

Read the license agreement, then click I Agree Go to Step 2



**STEP 2**

Fill in all the contact information provided in order form.

Make sure that the server's hostname is correct. It must be in the correct format ie, test.server.com.

Scroll down and make sure that at least two valid DNS resolvers. You can use our DNS resolvers

64.235.53.251

64.235.53.253 

Select the correct ethernet device.

When finished click Save and Go to Step 3



**STEP 3**

If you won't be adding any additional IP addresses, click Skip This Step

We can set up additional IP addresses later.



**STEP 4**

Choose which nameserver program you wish to use on this server. In most cases, you'll want to leave BIND as the nameserver.

Add nameserver domains as ns1.yourdomain.com and ns2.yourdomain.com in appropriate fields.

Verify that all of the IP addresses listed here are correct. Then, click each checkbox to add "A Entries" for all nameservers and the hostname.

When finished, Save & Go to Step 5

 

**STEP 5**

All the default services listed here are fine for most servers. However, You have the option of changing the FTP server and incoming mail server. Scroll through the services and change them, if you like, or just click Skip This Step above.

cPHulk should stay on. It will help prevent hacking attempts by those with malicious intent.



**STEP 6**

 Disk quotas help you keep track of hard drive usage on a per-user basis and enforce the space limits you give each account. Click on Use file system Quatas and Click Finish Setup Wizard to proceed to WHM.