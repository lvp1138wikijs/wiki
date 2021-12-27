---
title: Related Mail service ( Exim )
description: 
published: true
date: 2021-12-27T17:58:06.726Z
tags: 
editor: markdown
dateCreated: 2021-12-27T17:58:06.726Z
---

# Related Mail service ( Exim )


## Exim Message Reception and Delivery Log files

Exim writes three different logs, referred to as the main log, the reject log, and the panic log.

/var/log/exim_mainlog

The main log records the arrival of each message and each delivery in a single line in each case.

The format is as compact as possible, in an attempt to keep down the size of log files. Two-character flag sequences make it easy to pick out these lines. A number of other events are recorded in the main log.

Some of them are optional, in which case the log_selector option controls whether they are included or not. A Perl script called eximstats, which does simple analysis of main log files, is provided in the Exim distribution.The above log files receives an entry every time a message is received or delivered.

Rejections based on ACLs/Policies

: Receives an entry every time a message is rejected based on either ACLs orother policies (for example, aliases configured to :fail:)

/var/log/exim_rejectlog

The reject log records information from messages that are rejected as a result of a configuration option (that is, for policy reasons).

## Finding Exim Unexpected or Fatal Errors

 The below log file receives all entries exim doesn‘t know how to handle. It‘s generally a really bad thing when log entries are being written here, and they should be thoroughly investigated.

/var/log/exim_paniclog

When certain serious errors occur, Exim writes entries to its panic log. If the error is sufficiently disastrous, Exim bombs out after-wards. Panic log entries are usually written to the main log as well, but can get lost amid the mass of other entries. The panic log should be empty under normal circumstances. It is therefore a good idea to check it (or to have a cron script check it) regularly, in order to become aware of any problems.


## Useful Exim Commands

Find exim current version:

exim -bV
Delete All Frozen Emails:

exim -bpru|grep frozen|awk {’print $3′}|xargs exim -Mr
Force delivery of an email:

exim -M email-id
Force another queue run:

exim -qf
Force another queue run and attempt to flush the frozen messages:

exim -qff
View the log for the message:

exim -Mvl messageID
View the body of the message:

exim -Mvb messageID
View the header of the message:

exim -Mvh messageID
Remove bounced emails

cd /var/spool/exim/input
find . -type f -iname ‘*’ -exec grep -li "Failed" {} \; -exec rm {}\;


## Spamd failing Issues

If you find the ― spamd failing error on an exim restart.

 Solution When disabling spamd, the Cpanel create a file named /etc/spamdisable which may not get deleted on enabling the spamd feature again. Check the presence of the above said file.

 

The issue may also arise due to unavailability of the perl module Mail::SpamAssassin by

installing the the sameand on restarting the exim, the issue will be fixed.

1. /scripts/perlinstaller —force Mail::SpamAssassin

Run exim restart

2. /etc/init.d/exim restart

## Mail Error message: Error 550 The recipient cannot be verified

On servers running cPanel, some times it is found that mail sent to valid users is bounced back by the mail server.The bounce back messages will be similar to the following.

 

 PERM_FAILURE: SMTP Error (state 9): 550-”The recipient cannot be verified.Please check all recipients of this 550 message to verify they are valid.

 

If the email account does indeed exist, then it is need to run the following commands to correct the issue.

/scripts/updateuserdomains/scripts/mailperm

Also check the /etc/localdomains file and verify that the domain name is present. Also verify that the DNS line in the /var/cpanel/user/username contains the domain as well.

## Check outgoing emails send from particular email address

Check outgoing emails from particular email address

cat /var/log/exim_mainlog | grep “<= username@hostname” | wc -l

And incoming as

cat /var/log/exim_mainlog | grep “=> username@hostname” | wc -l

using current date you can find logs as

cat /var/log/exim_mainlog | grep “<= username@hostname” | grep 2009-06-20 | wc -l

