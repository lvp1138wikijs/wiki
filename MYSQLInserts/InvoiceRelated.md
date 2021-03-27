---
title: Invoice Related 
description: 
published: true
date: 2021-03-27T13:14:16.265Z
tags: 
editor: markdown
dateCreated: 2021-03-27T13:14:16.265Z
---

## Cancel normal Invoice
_INV_' : Replace with the correct invoice number.
    In the last insert accounting_history_s last letter “s” needs to be replaced with the first letter of customer username
    
>   delete from accounting_due_for_payment where invoice = _INV_;
> delete from accounting_due_for_payment_detail where invoice = _INV_;
> delete from accounting_history_s where sc_invoice = _INV_;
{.is-info}

*If you delete an invoice that is for multiple services but include a service that was canceled very recently and should not be charged, delete the invoice and the system will generate a new invoice next date without including canceled services. Be sure you don't do this for canceled services that must be payed*

## Cancel Service Charge Invoice [RHS] or One Time Invoice
> delete from accounting_due_for_payment where invoice = _INV_;
> delete from accounting_due_for_payment_detail where invoice = _INV_;
> delete from accounting_history_s where sc_invoice = _INV_;
> delete from supporttrack where sc_ticket = "_Ticket_ID_";
{.is-info}


## Add Bucks
Replace: _username_, _xx.xx_, _Notes_
> insert into credit_bucks (sc_username,sc_credit,sc_notes) values ("_username_","_xx.xx_","_Notes_");
>  
> Example
> insert into credit_bucks (sc_username,sc_credit,sc_notes) values ("zzzinuba","10.00","Survey credit");
{.is-info}

