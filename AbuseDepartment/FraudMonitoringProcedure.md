---
title: Fraud Monitoring Procedure
description: 
published: true
date: 2021-03-10T04:39:03.593Z
tags: 
editor: markdown
dateCreated: 2021-03-10T04:39:03.593Z
---

# Fraud Monitoring Procedure

**What is Fraud monitoring**?

```
We do Fraud monitoring for the new accounts, where the order details are suspicious and still we activated it. This should be daily monitoring. 
By monitoring an account for the mentioned time frame, we can conclude whether the order was genuine or fraud. 

```

**Following is the procedure you need to follow while doing Fraud Monitoring**:

Fraud Monitoring doc contains separate sheet for Cloud VM and Dedicated Servers. Enter the suspicious account details in the doc and then continue checking all accounts in the document for any fraud activity/complaints.


https://docs.google.com/spreadsheets/d/1lMxyyJK9uCLmcanx5XLuv4PHH6m4q_RVQlzgtyVb_ek/edit#gid=1

**First Scenario: If DMCA/Abuse Complaints received**:

```
Get the username > login to customer CP.
Collect the IP addresses and search in Gmail to see any complaints for that VM or Ded server IPs (including additional IPs).
If any complaints, check if an Abuse/DMCA complaint ticket is already opened. Add the ticket ID in the sheet with complaint details.
If ticket is not opened, you should open a ticket to customer and add the details in the Fraud monitoring Sheet.
Verify the complaint status on daily basis. Suspend account if needed. Add the details in sheet on each day.

```

**Second Scenario : if chargeback/paypal dispute/fraud charge complaints received**

```
Check in ticketing system with the username, if any chargeback/paypal dispute/fraud charge complaints received for the account
Add the ticket ID in the fraud monitoring sheet.
Verify account status (whether Suspended / Cancelled), update it in the sheet
Update sheet regularly after checking the account status.
Once the account is cancelled, move the entry to next sheet in the Fraud Monitoring name "Cancelled_Fraud"
```

**Third Scenario : More than 45 + Days**

```
If the monitoring has reached 45 + Days, check the status of the account on that day
Add it in 45 + Days column
Move that account to the 45 Days + sheet in the Fraud monitoring file
Add Last monitoring status only, no need to copy report from Day 1.
```

Fourth Scenario : No Complaints

```
If there are no complaints for the IP or no VMs, mention it in the sheet. 
Add it in 45 + Days column
Move that account to the 45 Days + sheet in the Fraud monitoring file
Add Last monitoring status only, no need to copy report from Day 1.
```

What all need to verify?

```
No of VMs in Running/OFF/Inactive state in the account
If Complaints received for any of the IP addresses under every VM
Total fund added (Paypal or CC)
If random new CC added to the account 
If any similar accounts are created by the Cx using different email address
```

