---
title: Error while creating redirect through cPanel
description: 
published: true
date: 2021-12-27T15:18:16.634Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:18:16.634Z
---

# Error while creating redirect through cPanel


If you try to set redirect from cPanel >> Redirects and gets the following error:

```
Apache detected an error in the Rewrite config.
Syntax error on line 11 of /home/user/public_html/.htaccess.xY4clswgX3Iyt_IeUfxIVwXQPNhLfxA0:
RewriteCond> directive missing closing '>
```
This error usually occurs when you try setting redirect rules from cPanel or  while enabling hotlink protection.

This is due to the .htaccess file with CRLF line terminators. For this cPanel feature to work the .htaccess file should have at least one empty line and with no CRLF line terminators. This can be verified by the following command.

```
# file .htaccess
.htaccess: ASCII text, with CRLF line terminators
```

To resolve the issue you can create a new file .htaccess with vi and copy the current contents in .htaccess to it.

Now try to verify the file type:

```
# file .htaccess
.htaccess: ASCII text
```

Now you will be able to create redirect rules and enable hotlink protection from cPanel.
