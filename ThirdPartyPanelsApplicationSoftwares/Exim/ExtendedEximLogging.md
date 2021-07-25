---
title: Extended Exim Logging
description: 
published: true
date: 2021-07-25T03:44:53.961Z
tags: 
editor: markdown
dateCreated: 2021-07-25T03:44:53.961Z
---

# Extended Exim Logging

By enabling Extended Exim Logging  It ads valuable logging information to your exim_mainlog file so that you can determine where messages are coming from, whos sending the message and from what directory on your server the user NOBODY is originating from, if your seeing mail leaving as nobody. In addition, it adds very useful information to exim_mainlog to help you decipher email coming and going. This is a very handy tool to find out the spamming on the server.

Here is an example;

```
2013-02-27 14:06:18 cwd=/home/username/public_html/forums 3 args: /usr/sbin/sendmail -t -i
2013-02-27 14:06:18 19W0QE-0001Nr-1b nobody@yourserversname.com from env-from rewritten as ""usersite.com" <minx@usersite.com>" by rule 1
```

The message above tells where the message came from, who sent it from my server, the user and the path it was called from. It also tells  how it was called and what it was renamed to before leaving my server. 

For enabling Extended Exim Logging, Please do the below steps.

1) Edit the file exim.conf using vi editor.

Find the line hostlist auth_relay_hosts = *

2) After hostlist auth_relay_hosts = * 

add the following

```
log_selector =
+address_rewrite
+all_parents
+arguments
+connection_reject
+delay_delivery
+delivery_size
+dnslist_defer
+incoming_interface
+incoming_port
+lost_incoming_connection
+queue_run
+received_sender
+received_recipients
+retry_defer
+sender_on_delivery
+size_reject
+skip_delivery
+smtp_confirmation
+smtp_connection
+smtp_protocol_error
+smtp_syntax_error
+subject
+tls_cipher
+tls_peerdn 
```

3) save the file.

4) Then restart exim using the command

```
/etc/init.d/exim restart 
```

Now tail your log and you will see additional information in the exim_mainlog file.

```
tail -f /var/log/exim_mainlog
```