---
title: How to Export the Mailman Mailing Lists
description: 
published: true
date: 2021-12-27T16:30:19.719Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:30:19.719Z
---

# How to Export the Mailman Mailing Lists


**In order to export Cpanel's Mailman mailing list, please do the following steps**:

1) Log into your account via SSH as root user.

2) Find your Mailman directory (usually located in /usr/local/cpanel/3rdparty/mailman/bin)

3) Execute the following command to copy the Mailman mailing list subscribers to a text file:

```
./list_members MAILINGLIST > ./subscribers.txt
```

Where MAILINGLIST = email address they use to subscribe (i.e. subscribe_domain.com).

4) Replace @ with _

For example, for the MailingList newsletter@nigna.com, you can execute the following command.

```
$ /usr/local/cpanel/3rdparty/mailman/bin/list_members newsletter_nigna.com > /home/trent/newsletter_nigna_com.txt
```

**In order to get the exact mailingList name, please do the following steps**:

```
cd /usr/local/cpanel/3rdparty/mailman/lists
ls
```

To export,

```
cd /usr/local/cpanel/3rdparty/mailman/bin
./list_members -o filename <mailing list name>
```

**In order to fix theMailman Mailing list permission issue**,

```
chmod 2775 -R /usr/local/cpanel/3rdparty/mailman/
```

**In order ti reinstall it, please do the following steps**:

```
/usr/local/cpanel/bin/mailman-install --force,.
```

**For Import Members to Mailman Mailing List, please do the following steps**: 

Add all email addresses one per line to the file /tmp/members.

```
cd /usr/local/cpanel/3rdparty/mailman/lbin
```

Then execute the command as shown in below:

```
./add_members -r /tmp/members list_domain.tld
```

Result was like:

```
Subscribed: one@domain1.com
Subscribed: two@domain2.com
Subscribed: three@domain3.com
```


