---
title: Exim:Locate Spam by Subject
description: 
published: true
date: 2021-07-24T05:45:58.235Z
tags: 
editor: markdown
dateCreated: 2021-07-24T05:45:58.235Z
---

# Exim:Locate Spam by Subject

The below command will print the emails which have the same subject from your exim mail log.

```
awk -F"T=\"" '/<=/ {print $2}' /var/log/exim_mainlog | cut -d\" -f1 | sort | uniq -c | sort -n
```

You will receive an output of the following format with the number of duplicate emails and the corresponding email subject displayed.

```
321 Gone on Vacation
232 Out of Office
1764 Loose Weight
```
Next we have to find the user sending out the spam emails:

```
grep "Loose Weigt" /var/log/exim_mainlog | awk '{print $5}' | sort | uniq -c | sort -n
```

We will get an output like:

```
1764 jerry@starsports.com
```

Next we need to find the IP address the user uses to send spam:

```
grep "<= jerry@starsports.com" /var/log/exim_mainlog | grep "Melt Fat Naturally" | grep -o "\[[0-9.]*\]" | sort -n | uniq -c | sort -n
```

You will get an output similar to

```
1764 192.12.14.55
```
Next we have to block the IP address from the server.

```
iptables -A INPUT -s 192.12.14.55 -j DROP
```

You will also have to change the password of that  email account as there are chances for the user to use your account again through a different IP to relay spam.








