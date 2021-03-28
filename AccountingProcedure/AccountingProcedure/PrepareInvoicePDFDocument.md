---
title: Prepare Invoice PDF Document
description: 
published: true
date: 2021-03-28T00:34:27.229Z
tags: 
editor: markdown
dateCreated: 2021-03-28T00:34:27.229Z
---

Right now our system not send invoices as in PDF document. Its just send a text email to the owner email address if an account is due. 

If a customer requested us to send the invoice as document. Then will prepare it manually. Just follow the procedure. 

Here are links to our invoice API

- For dedicated server bandwidth:   **https://secure.serverpoint.com/cgi-bin/cp/engine//api-invoice-band.cgi?invoicenumber=_invoiceID_&username=_username_**
- 
- for dedicated server:  **https://secure.serverpoint.com/cgi-bin/cp/engine//api-invoice-dedicated.cgi?invoicenumber=_invoiceID_&username=_username_**
- 
- for shared hosting: **https://secure.serverpoint.com/cgi-bin/cp/engine//api-invoice-shared.cgi?invoicenumber=_invoiceID_&username=_username_**
- 
- For  ColossusCloud:  **https://secure.serverpoint.com/cgi-bin/cp/engine//api-invoice-ccloud.cgi?invoicenumber=_invoiceID_&username=_username_**

**Replace Values**

**_invoiceID_** = replace it with correct invoice ID number 

**_username_** = Replace with customer usnername

**HowTo Download Invoice In PDF format**

- Modify the invoice url and open it in Google Chrome.
- Then try to print the document and save it as PDF