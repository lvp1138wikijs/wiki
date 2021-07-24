---
title: Mails redirected /dev/null **bypassed**
description: 
published: true
date: 2021-07-24T23:42:31.277Z
tags: 
editor: markdown
dateCreated: 2021-07-24T23:42:31.277Z
---

# Mails redirected /dev/null **bypassed**

Its an issue with spamassasign.

Edit the file /etc/mail/spamassassin/local.cf and add the following lines:

```
score FH_DATE_PAST_20XX 0.0
```

restart spamd and exim.