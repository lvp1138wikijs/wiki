---
title: Fraud Detection Procedure (New)
description: 
published: true
date: 2021-03-26T05:27:53.967Z
tags: 
editor: markdown
dateCreated: 2021-03-26T05:27:53.967Z
---

**From now on, we should approve all ColossusCloud orders, except the cases mentioned below**,



1. When the customer tries Different Credit Cards

2. Multiple Order placed from Same IP / Customer.

3. Pending PayPal payments (echeck payments need to arrive)

4. Orders including domains with trademarked names in them (Paypal, Bank name, etc.)

5. If orders start coming in from our IPs, it's a sign of fraud.

6.  AVS failed on them (Check Stripe for details)

7. CVC check is Failed (in multiple transaction, check Stripe for details )

8. If the IP is of a Hosting Provider

> **While checking Stripe**
> 
> **You should anyway be browsing through all payments done every day, In case there's a user who's payment is keep on getting failed after 1st transaction or so then do keep a close watch as it's suspicious**.
> 
> **According to Peter, If you say the accounts were due right away, and it's the same credit cards, then that's suspicious.  A legit customer would not let the credit card stop working**
{.is-info}

> Quick Tip
> 
> For Fraud Orders look for portion of users if they sounds suspicious .. as in jason1 jason2 jason3 etc. may be they are same customers placing orders again and again
{.is-info}

**As we are Activating most of the orders, we have to keep a close watch on Abuse reports**.

**We have to closely monitor the orders which looks little suspicious to us. Find below the cases that makes an order suspicious**,

- IP Location mismatch
- 
- IPs of hosting Provider
- 
- Order from Female user
- 
- Temporary emails address associated with the order.

 

**Ps. If we are getting abuse complaints from the new suspicious orders, It’s a true sign of Fraud and we should cancel such orders immediately**.
