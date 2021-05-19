---
title: How To Secure Windows Nameserver
description: 
published: true
date: 2021-05-19T06:04:06.389Z
tags: 
editor: markdown
dateCreated: 2021-05-19T06:04:06.389Z
---

# How To Secure Windows Nameserver
 

Make sure that you use the latest version of DNS server.

 

You may run the followijng command to test the DNS server version run by a particular site:

```
 nslookup
 server dns_server_to_test
 set type=txt
set class="chaos"
version.bind.
```

***Restrict zone transfers***

When you use Microsoft's DNS service check the Notify tab of the Zone Properties dialog box.

Next  check the "Only Allow Access From Secondaries Included on Notify List" box.

Also do the same with secondary (slave) name servers .

However we cannot restrtict zone transfers for zones used as forwarders.

***Enable secure dynamic updates*** 

Follow these steps:

First Open the DNS snap-in.
Right-click the applicable zone in the console tree , and then click **Properties**
Next on the **General tab**, verify that the zone type is **Active Directory-Integrated**
Next in **Dynamic updates**, click the option **Secure only**.