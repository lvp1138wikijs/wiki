---
title: How to hide apache web server version
description: 
published: true
date: 2021-06-16T18:00:19.490Z
tags: 
editor: markdown
dateCreated: 2021-06-16T18:00:19.490Z
---

It is possible to hide apache web server version and other information.  This is done for security reasons.. It is not a good idea to broadcast the version of the software that you are running on the server.

In order to hide apache web server version, please do the following steps:

1) Open apache configuration file (httpd.conf)  using vi editor and then edit the two entries as follows.

```
ServerSignature Off

ServerTokens Prod
```

**ServerSignature Off** : tells apache not to display the server version on error pages, or other pages it generates.

**ServerTokens Prod** :  tells apache to only return Apache in the Server header, returned on every page request.

Then restart the httpd service.

