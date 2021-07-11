---
title: How to Backup and Restore using command line Interface
description: 
published: true
date: 2021-07-11T01:29:28.841Z
tags: 
editor: markdown
dateCreated: 2021-07-11T01:29:28.841Z
---

All backup created by Plesk by default stored under Plesk backup repository located on Plesk server.

For Plesk Linux/Unix, repository location:

```
/var/lib/psa/dumps/
```
Note: /var/lib/psa/dumps/ specified by the DUMP_D variable defined in the /etc/psa/psa.conf configuration file.

For example:

```
grep DUMP_D /etc/psa/psa.conf

# Backups directory

DUMP_D /var/lib/psa/dumps
```

For Plesk Windows, repository is located in the %plesk_dir%\Backup\ folder.

**To Back up whole Plesk server**

```
# /usr/local/psa/bin/pleskbackup –server -v

-v option show information about backup process
```

**To Back up Single domain in Plesk with mails, hosting files, configuration and Database**

```
#/usr/local/psa/bin/pleskbackup –domains-name yourdomain.com –v
```

**To Back up only mail configuration and content**

```
# /usr/local/psa/bin/pleskbackup –domains-name yourdomain.com –only-mail -v
```

**To Back up only hosting configuration and content without emails**

```
# /usr/local/psa/bin/pleskbackup –domains-name yourdomain.com –only-hosting –v
```

**To Back up selected resellers . If no resellers provided, back up all resellers on the server**.

```
# /usr/local/psa/bin/pleskbackup –resellers-name [Reseller logins name] –v
```

**To Back up selective resellers, clients and domains in Plesk** 

```
# /usr/local/psa/bin/pleskbackup –resellers-name –f resellersclient.txt –v (resellerclietns.txt is a file which contain list for resellers names per line )
```

```
# /usr/local/psa/bin/pleskbackup –clients-name –f clients.txt –v (clients.txt file which contains list for clients name per line )
```

```
# /usr/local/psa/bin/pleskbackup –domains-name –f domainsname.txt –v (domainnames.txt file which contain list of domains name per line)
```

