---
title: Fraud Detection Procedure
description: 
published: true
date: 2021-03-26T05:57:39.291Z
tags: 
editor: markdown
dateCreated: 2021-03-26T05:57:39.291Z
---

The procedure is same for Dedicated/Colossuscloud/web hosting Orders

> **Orders From Brazil**
> 
> Almost all orders from BRAZIL are frauds. Check them properly and inform Minerva. Also, ask Authentication Form if payment from a credit card
> 
> If payment from a PayPal address, if you have doubt, and PayPal email address and email address in order doesn't match, then just send an email to PayPal email address, asking to reply back to confirm order would be fine.
{.is-warning}

## Order Validation Steps

**STEP 1: Validate Order IP address**

> VPN IPs
> 
> Customers from some countries like China, use VPN to browse the internet. VPN IP is should be from a server. Do not think they are fraud. Validate the other details
> 
> The reason is, their governments block internet traffic and therefore people use VPNs to access all the websites over the internet.
> 
> If a customer like this and have only issue with IP address they are not fraud. If you have any doubt then you can contact  Ramsh
{.is-warning}


> **IPs of Hosting Companies**
> 
> If the IP belongs to any Web hosting company then there is a possibility of Fraud.. so keep a close watch
{.is-danger}

**Do a whois** on order IP address to check the country location. 

whois ip_address

or 

Go to http://www.ip2location.com/free.asp

Put the IP and click on find location.

Compare location with the address provided and validate is same country and not a hosting company.

**Do a port scan** on the IP.

Go to the website http://www.mxtoolbox.com/PortScan.aspx .

Put the IP and select the ports to scan. Then click on ScanPort

**Google IP address** and check if it is listed in any proxy website or spam forums.

If an order placed through a proxy site. It will show the IP of that proxy server not the original IP of the requester. Google the IP and check the ip if its is pointing to any proxy site. If yes, the order should be a fraud one.

**STEP 2: Validate Client Website/company name/Reference**

- Check if domain provided is already registered and have a website. You can verify it from http://www.internic.net/whois.html
- Google the domain and check where it is listed. if it's listing then load the site. If it's not working/ not registered then it is most likely fraud.
- Google company name if provided
- Check the referrer in order e.g. if the referrer is google.com.vn and order info is the US then it is most likely fraud.

> Contact Person
> 
> Also be a bit Alert if the order is from a Female user (we got some charge back in the past) as most of our Customers are Male
{.is-warning}

**STEP 3: Validate Card Payments**

> **Pre-Paid Cards**
> 
> We do not accept payment from prepaid / virtual / gift cards. The major cards are from entroypay, greedots, bitcoins, ecopayz, okpay, payoneer. There are many others too. Google about this. It is easy to identify. It do not show the bank name properly. It should be something like greedot, entropay, etc. Also can detect card type from the bin database too.
> 
> **Still, there are locations where Payment via credit cards are not common so we can activate orders paid via Prepaid cards in such cases**.
> 
> To see the popular payment methods of a country always check,
> https://www.paymentwall.com/en/payment-methods/
{.is-warning}

- If Customer tried multiple times with Different cards than a Possible Fraud
- If a customer tried multiple times with the same card then can be a possibility he's not able to clear the payment ... Activate the order in this case.

**Validate BIN details of Credit card**

> Important
> 
> Do not assume an order is a fraud just because of the Bin information. Bin information may not match depending on the information available on bindb.com.
> 
> Orders from outside the US may not match.
> 
> We must call back for the orders which are from the US and we detect them as a fraud.
> 
> Contact Ms. Minerva to call the customer. If not responding send a text from google voice/WhatsApp.
{.is-info}

**What is a BIN number**?

Bank Identification Number (BIN) or Issuer Identification Number (IIN) is the six digit number on a bank card that gives details about the issuer of the card. It holds information about the bank, the country where the bank is located, card brand (such as Visa, MasterCard etc.) and card type. When someone makes a purchase, the system identifies the issuer with the card BIN number. This number helps identify the reliability of the transaction.

Go to new ICP and get the first 6 digits of credit card. Then go to

- http://www.bindb.com/bin-database.html and enter 6 digits there
- Alternative link:: http://binbase.com/csv.php?module=search and enter 6 digits there.

It will show you the issuing Bank and its country of origin. Verify that the info matches with order information.

- Match country code
- Check the issuing Bank phone number. All US banks with start with 800 and 888.
- Sometimes customer provides a local phone number for their bank, in this case, always google the bank telephone number, it will show in google search it would be the real number.
- Check match bank name with BIN and check if the name is a COPY PASTE from BIN database. Then it probably a fraud one

> Please pay Special attention if the bank name is written in all UPPERCASE letters (Avoid bank with initials as in BOA (Bank of America), AMEX etc.), so it could be a copy and paste from a BIN database.
{.is-warning}

**Validate Payment from PayPal**

- In case of an order with PayPal payment, do not ask for AF. No one will feel easy to send it.
- If you have doubt and the account looks sheer suspicious and even the PayPal email address and email address in order doesn't match, then just send an email to PayPal email address, asking to reply back to confirm order would be fine.
- Don't straightaway send a PayPal verification mail to the customer if only the email ID doesn't match. Send verification mail if there are series of reason which brings it in  the room of fraud order.
- We can wait for longer time for PayPal order customer to respond since we have no time limit lika e credit card to void/refund. I would say, we can wait for 2-3 days foPayPalal orders.
- Paypal accounts do hack but paypal charge backs do not charge us any fine lika e credit card, more over paypal has its own fraud detecting system, they immediately pua t hold on payment if they detect suspicious activity in some payment.

**STEP 4: Validate Client Email Address**

Google the email address in the order and check is there any link related to phish [eg: link to phishtank]

- If the email Id belongs to a registered domain name, Check the domain name and if all looks good, execute the order and Monitor it.

> Important
> 
> if email Id belongs to a test email provider ( for example : lackmail.ru) there's a possible sign of fraud

**AF Followup to Customer**

If we don't get any update form the customer after sending them AF once please send a AF followup to the customer before Deleting the order,

**Format**:

================================

Greetings,

I'm Jay, customer support representative from ServerPoint.

We hope this email finds you well. We are writing you regarding your  pending ColossusCloud order with us. We are still awaiting your response with details related to the authorization form, kindly update so that we can proceed accordingly.

For any further information please feel free to contact as we’ll be more than glad to assist you.

Regards,
{.is-warning}




 