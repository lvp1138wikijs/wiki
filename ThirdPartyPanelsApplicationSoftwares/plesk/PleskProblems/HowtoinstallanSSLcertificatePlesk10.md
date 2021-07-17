---
title: How to install an SSL certificate? - Plesk 10
description: 
published: true
date: 2021-07-17T06:02:04.278Z
tags: 
editor: markdown
dateCreated: 2021-07-17T06:02:04.278Z
---

# How to install an SSL certificate? - Plesk 10


```
1. Login to your Parallels Plesk Panel
1. In the left hand menu, click on Tools & Settings
1. Click the SSL Certificates link
1. Click the Add SSL Certificate icon
1. Enter a certificate name and the settings for your Certificate Signing Request (CSR)
1. Click the Request button to generate the Private Key which your SSL issuer will need, or click Self-Signed to issue your own certificate.
1. Once you have the certificate codes, you can upload them in the "Upload certificate files" section and click the Send File button, or you can paste the codes in the "Upload certificate as text" section and click the Send Text button
1. Go back to Tools & Settings
1. Click the IP Addresses link
1. Click the IP related to your domain
1. For the "SSL certificate" drop down, select the name of your SSL certificate
1. Click the OK button
1. Go back to Tools & Settings
1. Under Server Management, click the Services Management link
1. Restart the Web Server (Apache) service
```