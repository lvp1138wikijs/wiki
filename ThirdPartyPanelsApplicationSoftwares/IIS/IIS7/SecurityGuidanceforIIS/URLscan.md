---
title: UrlScan
description: 
published: true
date: 2021-12-20T20:13:35.698Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:12:18.156Z
---

UrlScan is a security tool that restricts the types of HTTP requests that Microsoft Internet Information Services (IIS) will process. By blocking specific HTTP requests, the UrlScan security tool helps prevent potentially harmful requests from reaching the server. UrlScan is implemented as an ISAPI filter that screens and analyzes HTTP requests as IIS receives them. When properly configured, UrlScan is effective at reducing the exposure of IIS to potential Internet attacks.


> Note: Microsoft has now released UrlScan 3.1. This version updates earlier versions of UrlScan with additional features, including the ability to filter requests based on query strings - which can help mitigate SQL injection and other attacks that use a query string payload, and the ability to created custom rules that scan parts of your HTTP requests.
{.is-info}


Administrators may configure UrlScan to reject HTTP requests based on the following criteria:


- The HTTP request method or verb
- The file name extension of the requested resource
- Suspicious URL encoding
- Presence of non-ASCII characters in the URL
- Presence of specified character sequences in the URL
- Presence of specified headers in the request

When UrlScan denies a request it will log the action and the reason for the denial, along with additional information about the request – typically, the complete URL and IP address of the source of the request. When a denial occurs, IIS sends a "404 Object not found” response to the client. This simple response reduces the possibility of inadvertently disclosing information about the server to a possible attacker.