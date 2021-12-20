---
title: Socket Programming
description: 
published: true
date: 2021-12-20T21:07:41.833Z
tags: 
editor: markdown
dateCreated: 2021-12-20T21:07:41.833Z
---

# Socket Programming

### Create Socket

The socket command will create a socket,

```
socket( SOCKET, DOMAIN, TYPE, PROTOCOL ); 
```

DOMAIN: is PF_INET. .
TYPE: e.g  SOCK_STREAM for TCP/IP connection.
PROTOCOL:  e.g (getprotobyname('tcp'))[2])

### Socket Bind

The following code binds a socket to an address:

```
 bind( SOCKET, ADDRESS ) binds a network ADDRESS to a SOCKET.
```
The ADDRESS  part contains three fields:

ADDRESS family

port number 

and 

IP address
