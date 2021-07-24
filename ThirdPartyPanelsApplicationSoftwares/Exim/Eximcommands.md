---
title: Exim commands
description: 
published: true
date: 2021-07-24T06:03:03.761Z
tags: 
editor: markdown
dateCreated: 2021-07-24T06:03:03.761Z
---

# Exim commands

**Exim Useful Commands**

The following are the useful commands for exim

- Print a count of the messages in the queue:

```
root@localhost# exim -bpc
```

- Print a listing of the messages in the queue (time queued, size, message-id, sender, recipient):

```
root@localhost# exim -bp
```

- Print a summary of messages in the queue (count, volume, oldest, newest, domain, and totals):

```
root@localhost# exim -bp | exiqsumm
```

- Print what Exim is doing right now:

```
root@localhost# exiwhat
```

- Start a queue run:

```
root@localhost# exim -q -v
```

- Start a queue run for just local deliveries:

```
root@localhost# exim -ql -v
```

- Remove a message from the queue:

```
root@localhost# exim -Mrm <message-id> [ <message-id> … ]
```

- Freeze a message:

```
root@localhost# exim -Mf <message-id> [ <message-id> … ]
```

- Thaw a message:

```
root@localhost# exim -Mt <message-id> [ <message-id> … ]
```

- Deliver a message, whether it's frozen or not, whether the retry time has been reached or not:

```
root@localhost# exim -M <message-id> [ <message-id> … ]
```

- Deliver a message, but only if the retry time has been reached:

```
root@localhost# exim -Mc <message-id> [ <message-id> … ]
```

- Force a message to fail and bounce as “cancelled by administrator”:

```
root@localhost# exim -Mg <message-id> [ <message-id> … ]
```

- Remove all frozen messages:

```
root@localhost# exiqgrep -z -i | xargs exim -Mrm
```

- Remove all messages older than five days

```
root@localhost# exiqgrep -o 432000 -i | xargs exim -Mrm
```

- Freeze all queued mail from a given sender:


```
root@localhost# exiqgrep -i -f luser@example.tld | xargs exim -Mf
```

- View a message's headers:

```
root@localhost# exim -Mvh <message-id>
```

- View a message's body:

```
root@localhost# exim -Mvb <message-id>
```

- View a message's logs:

```
root@localhost# exim -Mvl <message-id>
```

- Add a recipient to a message:

```
root@localhost# exim -Mar <message-id> <address> [ <address> … ]
```

- Edit the sender of a message:

```
root@localhost# exim -Mes <message-id> <address>
```

- Remove mails in queue from a particular sender:

```
exiqgrep -ir email@domain.com | xargs exim -Mrm
```


