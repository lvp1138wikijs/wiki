---
title: How to handle proofpoint listing?
description: 
published: true
date: 2021-03-10T00:29:34.240Z
tags: 
editor: markdown
dateCreated: 2021-03-10T00:29:34.240Z
---

# How to handle proofpoint listing?


**Symptoms**:

You will get a bounce-back message with the following error if your mail server IP is listed in proofpoints IP blocklist.

```
550 5.7.1 Email rejected because 1.2.3.4 is listed by Proofpoint.com
```

**How to check if your IP is listed in proofpoints IP blocklist**:

Use the form on the Proofpoint Dynamic Reputation IP Lookup Page to see if your IP address is currently blocked.

> Proofpoint Dynamic Reputation IP Lookup Page: https://support.proofpoint.com/dnsbl-lookup.cgi
{.is-info}


**Solution**:

If your IP address is listed on Proofpoint, It will be shown on the page.

> https://support.proofpoint.com/rbl-lookup.cgi?ip=1.2.3.4
> 
> NOTE: replace 1.2.3.4 with the correct IP address
{.is-info}

**Necessary steps to be taken to remove the IP address from the black list**:

- Take necessary steps to stop spamming on the server.
    a) Stop any account / sctipts spamming on the server.
    b) Remove any infection on cusomters computer whcih was causing the spamming.
- Submit a false positive using the form provided on the page.


> https://support.proofpoint.com/rbl-lookup.cgi?ip=1.2.3.4
> NOTE: replace 1.2.3.4 with the correct IP address
{.is-info}

> NOTE: Proofpoint is usually slow in removing the IP address from the blacklist, it might take 48 - 72 hrs to get the IP address removed from the blacklist.
{.is-info}
