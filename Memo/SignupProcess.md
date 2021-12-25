---
title: MEMO - changes to the sign up process for ColossusCloud | 10-Aug-16 
description: 
published: true
date: 2021-12-25T16:00:58.693Z
tags: 
editor: markdown
dateCreated: 2021-12-25T16:00:58.693Z
---

# MEMO - changes to the sign up process for ColossusCloud | 10-Aug-16



Changes are:

1- no more popup screen when you log in. Most prospective clients were just simply closing the screen without really reading it. Instead, that content is now in the main interface.

2- if you try to provision a VM, however, the payment popup screen will show up to allow the client to enter a credit card or make a paypal deposit.

3- for non-active clients, they won't see a way to enter a custom PayPal amount. They have to choose one of the pre-set amounts.

But the biggest change is the following: instant activation.

And this is a major change that will require changes in procedures.

When a client provides a credit card or makes a paypal deposit, they will be able to immediately create a virtual server. It was frustrating clients, and confusing them, the fact that they would still get errors when trying to deploy a virtual server, even though they had provided a credit card or made a paypal deposit. Clients don't want to wait.

So the process of approving or rejecting an order is now different.

APPROVING AN ORDER

- If you think the order is certainly not fraud, as before, you just click "approve" in the order management interface.

 

REJECTING AN ORDER

- if the client has no VM, then that's no problem. Just go ahead and click "delete" as usual.

- If the client does have a VM already being created, or already created, then it won't let you delete the order. You will see a new pull down menu with the options:

-- suspend account (if you suspect the account is certainly fraud)

-- void all credit card transactions (again, if you suspect the account is certainly fraud)

-- delete VMs (will initiate deletion of VMs, then 48 hours later, you can delete the order)


- If you think an account is fraud, then you do "suspend", then later, "void" and later on, delete their VMs.

As always, use GOOD judgement to decide if an order is fraud or not. If there is absolute evidence it is fraud, such as a client trying ten different credit cards, then you assume it's fraud. But because BIN doesn't match or paypal address doesn't match, those are NOT absolute reasons to consider an account fraud. They may be suspicious, but it's not reason to go ahead and shut down a client's account. You can wait a bit longer to verify if they really are fraud or not.

You can see screenshots of the changes here:

https://www.dropbox.com/sh/h1kfw3pylrrt46q/AAAtV2_sf0DOGeUhWLE-KEJda?dl=0

Under folder 4.1.6.
