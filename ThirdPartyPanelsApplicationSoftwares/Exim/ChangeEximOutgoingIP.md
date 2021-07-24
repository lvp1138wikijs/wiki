---
title: Change Exim Outgoing IP
description: 
published: true
date: 2021-07-24T23:05:46.539Z
tags: 
editor: markdown
dateCreated: 2021-07-24T23:05:46.539Z
---

# Change Exim Outgoing IP

## Change Exim’s Sending IP

You can change the server’s IP address for sending email. If you already have an IP set up on your server, then you can simply change the interface lines in your /etc/exim.conf file and restart exim:

Here the steps;

- vi /etc/exim.conf
- Search for remote_smtp:
- You will find something like this

```
remote_smtp:
driver = smtp
interface = ${if exists {/etc/mailips}{${lookup{$sender_address_domain}lsearch*{/etc/mailips}{$value}{}}}{}}
helo_data = ${if exists {/etc/mailhelo}{${lookup{$sender_address_domain}lsearch*{/etc/mailhelo}{$value}{$primary_hostname}}}{$primary_hostname}}
 
dk_remote_smtp:
driver = smtp
interface = ${if exists {/etc/mailips}{${lookup{$sender_address_domain}lsearch*{/etc/mailips}{$value}{}}}{}}
helo_data = ${if exists {/etc/mailhelo}{${lookup{$sender_address_domain}lsearch*{/etc/mailhelo}{$value}{$primary_hostname}}}{$primary_hostname}}
dk_private_key = "/var/cpanel/domain_keys/private/${dk_domain}"
dk_canon = nofws
dk_selector = default
```

In the above example, just **comment out the interface lines and replace them with**:

- **interface = xx.xx.xx.xx**

Note : Replace xx.xx.xx.xx with the exact ip.
