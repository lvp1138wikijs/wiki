---
title: FTP Error - 1-al: No such file or directory
description: 
published: true
date: 2021-05-23T04:08:07.795Z
tags: 
editor: markdown
dateCreated: 2021-05-23T04:08:07.795Z
---

Sometimes customers report following error with FTP software in MAC (Fetch):

```
Fetch could not get the file list because the FTP server sent an
unexpected response. (Check the Fetch Transcript window for more information. 
Server responded: “ -al: No such file or directory”)
```

Solution:

```
To fix that problem uncheck the "Use 'LIST -al' command to reveal hidden items" box in the Miscellaneous section of Fetch Preferences. 

```

Reference Link :

```
http://fetchsoftworks.com/fetch/messageboard/1-al-no-such-file-or-directory-unexpected-response
```

Reference Ticket :

```
https://secure.serverpoint.com/tickets/staff/index.php?/Tickets/Ticket/View/334957/inbox/11/6/-1
```
