---
title:  SWIP - ARIN 
description: 
published: true
date: 2022-01-21T12:46:55.586Z
tags: 
editor: markdown
dateCreated: 2022-01-21T12:46:55.586Z
---


# Shared WHOIS Project (SWIP):
Updating Internet Protocol (IP) Address Space Information in the WHOIS Database

SWIP is the process that Internet Service Providers (ISPs) use to submit customer IP space reassignment information to WHOIS. The purpose of SWIP is  to ensure effective, efficient maintenance of records on IP address space.

SWIP can be done for a block of 8 or more then 8 ips.

To submit SWIP, you need to fill following template

 
> Template: ARIN-NET-MOD-5.0
> **  As of March 2011
> **  Detailed instructions are located below the template.
> 00. API Key:
> 01. Registration Action (M or R):
> 02. IP Address and Prefix or Range:
> 03. Network Name:
> 04. Origin AS:
> 05. Tech POC Handle:
> 06. Abuse POC Handle:
> 07. NOC POC Handle:
> 08. Public Comments:
> END OF TEMPLATE

 

and email it to hostmaster@arin.net using noc@premianet.com email address.

After sending email, keep checking gmail, since you will receive approval or rejection email to gmail.

 
> SAMPLE TEMPLATE
> Template: ARIN-NET-MOD-5.0
> **  As of March 2011
> **  Detailed instructions are located below the template.
> 00. API Key:
>  
> 01. Registration Action (M or R): M
> 02. Network Name: SERVERPOINT-CUSTOMER-RAPIDVPN
> 03. IP Address and Prefix or Range: 64.235.42.132 - 64.235.42.195
> 04. Origin AS: 26277
> 05. Customer Name: Robin Lieser
> 06. Customer Address: 37b New Cavendish
> 06. Customer Address:
> 07. Customer City: London
> 08. Customer State/Province: EG
> 09. Customer Postal Code: W1G 8JR
> 10. Customer Country Code: UK
> 11. Public Comments:
> END OF TEMPLATE

If you are assigning SWIP to customer then use M in

*Registration Action (M or R)*
 

and If you are removing SWIP from customer and setting it back to us then use R

M = Modify
R = Remove
