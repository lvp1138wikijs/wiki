---
title: Configure HTTP Settings
description: 
published: true
date: 2021-12-16T20:02:26.069Z
tags: 
editor: markdown
dateCreated: 2021-12-16T20:02:26.069Z
---

# Configure HTTP Settings

> Applies To: Windows 7, Windows Server 2008, Windows Server 2008 R2, Windows Vista
{.is-info}

IIS can provide a better user experience for visitors to your Web site by letting you control the content that is returned when a Web page is requested. IIS also lets you deliver custom error messages whenever a problem occurs with your Web site or an application on your Web site. Common HTTP features include the following areas:

**Default Document**

Default documents let you specify a list of files that can be returned to client browsers when a document name is not specified in requests.

**Directory Browsing**

 Directory browsing lets you return a directory listing to client browsers when a document name is not specified in requests.


**HTTP Error Pages**

Custom error pages let you provide a friendly or a more informative response to visitors to your site when the content requested cannot be accessed. You can change the default settings in IIS and configure IIS to return a custom error page whenever an HTTP error occurs.

**HTTP Redirection**

Redirection refers to the process of configuring the Web server to issue a redirect message to the client, such as HTTP 302, which instructs the client to resubmit the request for a new location. You can configure redirect rules that will cause the end user's browser to load a different URL than the one originally requested.

**HTTP Response Headers**

HTTP headers are name and value pairs that contain information about a requested page. This information includes the HTTP version, date, and content type. You can create custom headers to pass special information in responses to clients.

**MIME Types**

MIME types identify the types of content that can be served to a browser or a mail client from a Web server. You can add, edit, or delete MIME types.