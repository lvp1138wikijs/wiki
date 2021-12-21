---
title: Fatal error: Allowed memory size of x bytes exhausted (tried to allocate xbytes)
description: 
published: true
date: 2021-12-21T16:47:18.288Z
tags: 
editor: markdown
dateCreated: 2021-12-21T16:47:18.288Z
---

# Fatal error: Allowed memory size of x bytes exhausted (tried to allocate xbytes)


> Fatal error: Allowed memory size of x bytes exhausted (tried to allocate xbytes)
{.is-info}

The above error normally occurs when PHP tries to process a big database records or when importing or exporting.

In order to resolve this error, you can do type fixes. One is to increase PHP memory limit of the account by using a custom php.ini file. But sometimes it won't work.

If it didn't work, then you can fix the error by increasing the memory of the particular PHP script (displayed in error message) by adding an additional line at the top of the script:


> ini_set(”memory_limit”,”32M”);   (Change the value based on the error message).
{.is-info}

Now browse the page again, perform the operation again. It will just work fine if you have set correct value based on the error message.
