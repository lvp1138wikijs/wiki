---
title: SSL Order / Renew / Reissue / Cancel Procedures
description: 
published: true
date: 2022-04-15T22:16:16.911Z
tags: 
editor: markdown
dateCreated: 2021-06-03T15:03:34.722Z
---

# SSL Order / Renew / Reissue / Cancel Procedures
What is SSL certificate 

The Secure Socket Layer protocol was created by Netscape to ensure secure transactions between web servers and browsers. The protocol uses a third party, a Certificate Authority (CA), to identify one end or both end of the transactions. This is in short how it works.

- A browser requests a secure page (usually https://).
- The web server sends its public key with its certificate.
- The browser checks that the certificate was issued by a trusted party (usually a trusted root CA), that the certificate is still valid and that the certificate is related to the site contacted.
- The browser then uses the public key, to encrypt a random symmetric encryption key and sends it to the server with the encrypted URL required as well as other encrypted http data.
- The web server decrypts the symmetric encryption key using its private key and uses the symmetric key to decrypt the URL and http data.
- The web server sends back the requested html document and http data encrypted with the symmetric key.
- The browser decrypts the http data and html document using the symmetric key and displays the information.

## How to Order New / Renew SSL Certificates
- [Shared Hosting account](/TechnicalSupport/SSLCertificates/ProcedureSharedandWebHostingPlans/)
- [Dedicated / VPS account](/TechnicalSupport/SSLCertificates)

## How to Reissue / Cancel Newly ordered SSL Certificates

- [How to reissue SSL?](/TechnicalSupport/SSLCertificates/reissuessl)
- [How to Cancel and Get Refund on Newly Ordered SSL Certificate](/TechnicalSupport/SSLCertificates/SSLOrderRenewReissueCancelProcedures/CancelandGetRefundNewOrder)
