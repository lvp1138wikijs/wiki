---
title: Block Ipaddress for a website using .htaccess
description: 
published: true
date: 2021-06-16T16:45:55.684Z
tags: 
editor: markdown
dateCreated: 2021-06-16T16:45:55.684Z
---

If you want to block an ipaddress or a range for a particular website you can do it using .htaccess file for the domain.

1) Create or edit the existing .htaccess file in the document root of the website ( usually /public_html )

2) Add the following line at the top of the file and exit it.

```
order allow,deny

deny from IPAddress

allow from all
```
Please replace IPAddress with the actual ipaddress that you need to block and it should be done.

If you would like to block multiple IPs, you can insert the following lines instead:

```
order allow, deny

deny from IP1

deny from IP2

deny from IP3

allow from all
```

Replace IP1,IP2, IP3 with the actual ipaddress that you need to block

You can block an IP range as well. For example if you want to block an iprange 10.0.0.0/24 you can enter the following instead of listing 256 ipaddress seperately

```
order allow,deny

deny from 10.0.0.0/24

allow from all
```


