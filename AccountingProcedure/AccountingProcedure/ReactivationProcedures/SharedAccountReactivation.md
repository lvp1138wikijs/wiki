---
title: Shared Account Reactivation
description: 
published: true
date: 2021-03-28T01:39:57.872Z
tags: 
editor: markdown
dateCreated: 2021-03-28T01:01:08.643Z
---

**Reactivation procedure of Canceled / Suspended Shared Account**

If a customer ask for re-activating the his accounts , then please do the following procedure before re-activate.

1. Login to ICP » Click on Shared Active and check the domain domain.com list there
1. If its listing, then check the account Type . Its should be **Level1** for suspended account . Tell customer pay the due amount. Once its completed , then system will reactivate it automatically.
1. If its not listing in the shared active. Then search in Shared cancel
1. If its listed . It can be restore with in 5 days after cancellations. Do the following
   a. Check the cancellation date.
   b. We keep cancelled account backup for 5 days after the        account cancelled. If client contact in that 5 days ,          then its possible to reactivate .
   c. Contact James to check the available backup
   d. Contact Minerva for approval.
   e. Once its approved , then Inform customer customer pay for restoration fee $25 and monthly charge of account
   
5. To reactivate the account then run this mysql inserts.

> Old Plans
> 
> Please Note Eternal, Personal accounts: are old shared accounts we no longer offer. We no longer advertise this plan on our site, we cannot reactivate it since we no longer offer the plan
{.is-warning}

### Reactivation of Resold Account


If a customer contact us to to reactivate the resold account , then do the following

1. **Main Account is Active and Resold Account is Suspended**

- Then check resold domain account type in ICP » Shared Active and check .Its should be Level1 for suspended account . Tell customer pay the due amount. Once its completed , then system will reactivate it automatically.

2. **Main Account is Cancelled and the Resold is Available to Reactivate**.

  1. Then we can convert this account to as main account . Send client this [reply](/Templates/Reactivationrepliesforshared)

  2. Once customer reply back with details , then prepare the following inserts and send to Minerva. The NPD should be current date, so that system will generate a new invoice in the next billing run.
  3. Once query run , then provide client the login detail and procedure to add credit card to their account

3.**MAIN Account is Active and Resold Account is Cancelled**

There is no way to reactivate a resold account. Customer can order a "new resold" account with same domain name.

If client want the backup of data then do the following

- Check the cancellation date in ICP » Shared Cancel
- We keep cancelled account backup for 5 days after the account cancelled. If client contact in that 5 days , then its possible to restore backup .
- Contact James to check the recent Backup Available.
- Then Inform customer about the available backups and tell them pay for restoration fee $35 + resold account charge
- Once confirmed, inform James to restore data of account to new account.
- Make sure to explain James, that data has to be restored in "new resold" account with old domain name, since new account will have new location on server, and backup will have to be restored on new location.


> Please Note:
> 
> If 5 days were over, then there is no chance to restore. The accounts is permanently removed from the server. Customer will have to start over. He want to place order from website if they want to proceed. Then send this [reply](/Templates/Reactivationrepliesforshared) to customer
{.is-warning}

