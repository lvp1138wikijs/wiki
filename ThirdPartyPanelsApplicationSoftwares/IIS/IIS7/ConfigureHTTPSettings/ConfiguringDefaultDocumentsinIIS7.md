---
title: Configuring Default Documents in IIS 7
description: 
published: true
date: 2021-12-20T17:44:42.711Z
tags: 
editor: markdown
dateCreated: 2021-12-20T17:44:42.711Z
---

> Applies To: Windows 7, Windows Server 2008, Windows Server 2008 R2, Windows Vista
> 
{.is-info}

If a client accesses your Web site or Web application without specifying a document name (for example, requesting http://www.contoso.com/ instead of http://www.contoso.com/default.html), you can configure IIS to serve a default document, such as default.htm. If you list more than one default document, IIS reviews the default document list (in order) until it finds a match in the directory and then serves the file to the client.
When both default documents and directory browsing are disabled, client browsers receive a 404—File Not Found error because the Web server cannot determine which file to serve and cannot return a directory listing. However, if default documents are disabled but directory browsing is enabled, client browsers receive a directory listing instead of a 404—File Not Found error.