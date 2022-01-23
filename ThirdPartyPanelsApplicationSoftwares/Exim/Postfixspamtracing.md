---
title: Postfix spam tracing
description: 
published: true
date: 2022-01-23T06:10:59.583Z
tags: 
editor: markdown
dateCreated: 2022-01-23T06:10:59.583Z
---

# Postfix spam tracing.

Get the mailids of all email currently in queue:

postqueue -p|egrep "[A-F0-9]{11}"|awk '{print $1}'
Get the count of emails in queue:

mailq | tail -n 1

or

postqueue -p|egrep "[A-F0-9]{11}"|awk '{print $1}'|wc -l
List all message in queue:

postqueue -p
To flush the mail queue:

postfix -f
To remove all mails from the queue:

postsuper -d ALL
 

To remove all mails in the deferred queue:

postsuper -d ALL deferred
To view message content in queue with id xxxxxxxxxxx

postcat -vq  xxxxxxxxxxx
 

To track httpd php spamming using sendmail

You need php5.3.0 or above for this to work.
Add seting below in php.ini

mail.add_x_header = On
mail.log = /var/log/php-mail.log


once done

touch /var/log/php-mail.log
chmod 777 /var/log/php-mail.log

tail -f 

/var/log/php-mail.log