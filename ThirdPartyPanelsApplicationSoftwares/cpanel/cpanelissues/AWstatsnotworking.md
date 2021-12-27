---
title: AWstats not working/updating - CPanel
description: 
published: true
date: 2021-12-27T14:28:18.847Z
tags: 
editor: markdown
dateCreated: 2021-12-27T14:28:18.847Z
---

# AWstats not working /updating - CPanel

If AWstats is not working /updating in CPanel, please do the following fixes:

- First check permission of /usr/local/cpanel/3rdparty/bin/awstats.pl, it should be 755.

- Then to update awstats and webalizer run the following script :

```
# /scripts/runweblogs user_name
```

- If that didn't work try fixwebalizer script :

```
# /scripts/fixwebalizer
```

- If that doesn’t update stats, then check domlogs of the domain and see if it is up to date.

```
# /scripts/runstatsonce
```

- If none of the above fixes the issue and the awstats page for the domain is still showing the old date for last update, run the following command :

```
# /usr/bin/perl /usr/local/cpanel/3rdparty/bin/awstats.pl -config=/home/user_name/tmp/awstats/awstats.domain.com.conf -LogFile=/usr/local/apache/domlogs/domain.com -update
```
**
Note: Replace domain.com with your domain name and replace user_name with your cPanel username.**
