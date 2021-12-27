---
title: Related to SSL
description: 
published: true
date: 2021-12-27T19:46:03.621Z
tags: 
editor: markdown
dateCreated: 2021-12-27T19:46:03.621Z
---

# Related to SSL

**CA (Certificate Authority) Bundle**

A file on your server that verifies that your public and private keys were issued by a trusted entity.If your Certificate Authority sent you a CA bundle file, you can install it to your server using

WHM‘s Install a SSL Certificate and Setup the Domain feature, or the Manage Service SSL Certificates feature.

**Install a SSL Certificate and Setup the Domain**

 When you use this feature, WHM will automatically install your SSL certificate and private key in the correct directories. You may either paste the certificate and key into the fields on the screen yourself, or allow WHM to retrieve them.It is very important that your SSL certificate and private key reside in the correct directories because if they do not,your server will remain unauthenticated, leaving your visitors at risk.

