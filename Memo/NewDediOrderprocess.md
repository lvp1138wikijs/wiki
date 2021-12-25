---
title:  MEMO - new dedicated order process | 22-May-2016 
description: 
published: true
date: 2021-12-25T16:03:17.838Z
tags: 
editor: markdown
dateCreated: 2021-12-25T16:03:17.838Z
---


The old order process for dedicated servers is now gone. And I think you can agree the new one is a great improvement over the old one.

Old one:
https://secure.serverpoint.com/cgi-bin/ordersystem/engine.cgi?sc_execute=1&template_file=addproduct&productid=dualintel

New one:
https://secure.serverpoint.com/cgi-bin/gen3cpdev/engine/order-dedicatedhosting.cgi?productid=e31220v2&ramid=e3ram8&chassisid=1u1x35s

In case you haven't seen the old one in a while...
Prices and specs have been updated for both "business" and "enterprise" servers:

http://www.serverpoint.com/en/dedicated-server/value-dedicated-servers.phtml
http://www.serverpoint.com/en/dedicated-server/enterprise-dedicated-servers.phtml

The servers you see there are the same models we've offered for quite some time now. However, we are currently evaluating and testing new models, new CPUs, new boards, chassis, etc. I hope we have those new models available in a week or two. Travis, Chris and Aaron are all working on that.
Classic servers:

http://www.serverpoint.com/en/dedicated-server/cheap-dedicated-servers.phtml

Have not been updated, and still link to the old order process. The reason is that we do plan on eliminating those within two weeks or so, once we release our new serverpoint.com website.
The purpose of this new order process is:

- it is now integrated into the client portal's code, instead of separate software as before, making it easier for us to update and maintain.
- It is very easy to update models and prices
- it will hopefully encourage upselling, specially of RAID storage
- it allows multiple servers to be ordered simultaneously
- it's nicer looking
This new order process is still missing a few things:

- Ability for existing clients and resellers to log in. I will hopefully add that today or tomorrow.
- Do not allow selection of non-centos if client chooses cpanel
- It does not force the selection of the chassis; client can still downgrade it (add disks to see how the chassis changes)
- it's missing a text box to allow custom RAID instructions
- it's missing photos of each chassis the client can choose
- it's missing prepaid discounts for 3, 6 and 12 month prepayments
- selection of additional IP numbers and bandwidth packages
- selection of a managed support plan
- selection of backup services (we are working on a new backup software and infrastructure)
- windows 10, windows enterprise and windows data center are missing
- ability to pay a fee for a custom operating system install
- ability to choose installation of vmware, cloudstack, plesk, and some other third party platforms

Lots missing... I know. It ain't easy.
 
A new interface in the new admin panel is being worked on to managed and deliver these orders. The interface is already there, and fully tested. However... DO NOT DELIVER OR DELETE ORDERS WITHOUT INFORMING ME FIRST.
 

Some notes:
- custom orders: most custom orders should be configurable through this interface and should give you accurate pricing. IF any custom order does NOT fit within the specs offered by this interface, then we need to either add the missing options, or, suggest something different to the client.
- the prices provided by this interface are for all clients; yes, prices were lower before, but we won't honor those prices anymore. As always, there may be an exception or two, but that will be rare and consult me or Minerva for approval, for now.
