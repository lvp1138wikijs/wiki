---
title: Error Messages in IIS 6.0
description: 
published: true
date: 2021-09-22T04:52:01.549Z
tags: 
editor: markdown
dateCreated: 2021-09-22T04:52:01.549Z
---

You can configure Internet Information Services (IIS) to send default HTTP 1.1 error messages or custom error messages. Custom error messages can be mapped to a file name or to a URL.

This section includes the following information:

## Enabling Standard HTTP 1.1 Error Messages

**To enable standard HTTP 1.1 error messages **

1. In IIS Manager, double-click the local computer; right-click the Web site, virtual directory, directory, or file for which you want to enable standard HTTP 1.1 error messages; and then click Properties.

1. Click the Custom Errors tab.

1. In the Error messages for HTTP errors list, click the HTTP error(s) that you want to change to standard HTTP 1.1 error(s), click Set to Default, and then click OK.

## Configuring Custom Error Messages

**To configure custom error messages** 

- In IIS Manager, double-click the local computer; right-click the Web Sites folder, an individual Web site folder, a virtual directory, or a file; and then click Properties.

> Note
> Configuration settings made at the Web Sites level are inherited by all of the Web sites on the server. You can override inheritance by configuring the individual site or site element.

- Click the Custom Errors tab.
- In the Error messages for HTTP errors list, click the HTTP error that you want to change, and then click Edit
{.is-info}


> Note
> The following errors are not customizable: 400, 403.9, 411, 414, 500, 500.11, 500.14, 500.15, 501, 503, and 505.
> 
{.is-info}

- In the Message Type list box, click either File to return a custom error file or URL to direct the request to a custom error URL on the local machine.

> Important
> If your custom error is an .asp page, you must select URL. If you do not select URL, you risk returning .asp source code to the client.
{.is-info}

- If you selected File, type the path to the file or click Browse to navigate to the file. Custom error messages are installed by default to the systemroot\Help\IisHelp\Common folder. The file names are numbers that correspond to the specific HTTP errors; for example, 400.htm, 401-1.htm, and so on.

or

If you selected URL, type the path to the Web site or virtual directory. The URL must be a Web site or a virtual directory on the local machine. In addition, the custom error URL must exist in the application pool that directs the request to the custom error URL. If you store custom error pages in a virtual directory, that virtual directory must run in the same application pool as the rest of your Web site. Otherwise, the worker process cannot serve the custom error page when it is requested.

- Click OK, and then click OK again.


