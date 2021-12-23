---
title: cpanel: incorrect database size
description: 
published: true
date: 2021-12-23T19:07:34.626Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:07:34.626Z
---

# cpanel: incorrect database size

If your database is showing the wrong database size, i.e it always shows 0mb then follow the procedure below to correct the issue:

Login to your WHM

Then go to , WHM >> Main >> Server Configuration >> Tweak Settings >> SQL >>

Then select the option "Include databases in disk usage calculations " and set it to ON.
 


Finally run the command:

/scripts/update_db_cache