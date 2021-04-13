---
title: Handling Fraud order tickets
description: 
published: true
date: 2021-04-13T16:24:59.304Z
tags: 
editor: markdown
dateCreated: 2021-04-13T16:24:59.304Z
---

# Handling Fraud order tickets:

1) When a new order is found to be sure fraud with active VMs in the account, suspend it, void the payment and delete the account.
2) As you know, it will take 72 hours for complete removal of deleted VM from the account.
3) There is no need to keep those tickets in open queue. Close/Process the order tickets.
4) Schedule in Gmail to check the account after 72 hours to confirm deletion of VM and then cancel the Order.
5) DO does not forget to add NOTIFICATION in the schedule.
6) Add memo in order execution page regarding Gmail schedule. (something like : Scheduled in Gmail to delete this order on "DATE", once the VM is removed fully. ) 

Reference for Fraud order Tickets:

JMW-457-68936

GJP-381-28499

IQO-725-16608