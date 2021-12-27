---
title: Common Problems
description: 
published: true
date: 2021-12-27T17:19:26.169Z
tags: 
editor: markdown
dateCreated: 2021-12-27T17:19:26.169Z
---

# Common Problems


## Cpanel WHM: License expired error

If License expired error is encountered while accessing the cpanel/whm, it can be fixed by following below
mentioned steps:
 

1. Check whether the license is expired.
This is the most obvious cause and simple to verify. Access the URL =http://verify.cpanel.net/‘ and check the IP of
the server.


2. If it is ?active, Run the following command:
 
$ /usr/local/cpanel/cpkeyclt

This should promptly return to the command line with no messages. If it takes a while, then there is likely aconnectivity issue between your server and the licensing server.


3. In that case, check whether the firewall is blocking connections to the licensing server.Verify that port 2089 TCP outgoing traffic is allowed in the firewall rules.


4. If you‘re not sure that your firewall is properly configured, then the best thing to do is temporarily flush your
firewall rules. Before flushing the firewall rules, you need to save the firewall rules enabled in the server.
$ /etc/init.d/iptables save
After that you can flush your firewall rules using the command
$ iptables -F

## Finding Spammer on Cpanel Server

Follow the steps given below to catch Spammers sending mails from scripts ( nobody emails ) :-

1. Edit /etc/exim.conf
2. find "log_selector", comment the line with # and add below line

log_selector = +address_rewrite +all_parents +arguments +connection_reject +delay_delivery +delivery_size +dnslist_defer +incoming_interface +incoming_port +lost_incoming_connection +queue_run +received_sender +received_recipients +retry_defer +sender_on_delivery +size_reject +skip_delivery +smtp_confirmation +smtp_connection +smtp_protocol_error +smtp_syntax_error +subject +tls_cipher +tls_peerdn

3. restart exim
4. Run below command to watch outgoing emails
tail -f /var/log/exim_mainlog | grep cwd

Note: cwd stands for current working directory.
This is quite normal: cwd=/var/spool/exim
This warrants investigation, but might be legit: cwd=/tmp
This is generally bad: cwd=/home/h4x0r/public_html/forums/tmp

if the spammer is not spamming using formmail scripts then go through following steps :-

1. Get the message ID from the header of the spam. It should be in format like 1DWJj4-00042i-74 ( this is the most important step else all thats given below is crap )

2. grep exim_mainlog with the message ID ( Ex : grep 1DWJj4-00042i-74 /var/log/exim_mainlog )

3. Check the time on which the spam was sent and also check all that is shown after grep.

4. If you find out the domain name or path of the scripts from exim_mainlog then go ahead and suspend the spammer, else proceed to step 5.

5. Use this message ID to check the original message or bounced message in /var/spool/exim/input/. You should see 2 files there, one with -D at end and one with -H at the end. ( Ex : /var/spool/exim/input/4/1DWJj4-00042i-74-D & /var/spool/exim/input/4/1DWJj4-00042i-74-H ) This 2 files will have all the information that was sent in the spam message and if it was sent using mailing list then you will catch the username of spammer in auth_sender part of this files. If it shows nobody then its your bad luck Proceed to step 6.

6. If exim_mainlog shows the spams originating from /tmp of the server and check the file in /tmp of the server. wner of the file will be seen as nobody:nobody. Take down the time of creation of file. This time is what we need to find out who uploaded the script. You will need to convert this time into the time format of /usr/local/apache/logs/error_log & then in the format of the domlogs located at /usr/local/apache/domlogs/*

7. for file in /usr/local/apache/domlogs/*; do cat $file |grep “example”; done; ( you cannot do direct grep for the query here as it will give error that the arguement list is too long )

8. If the results in step 2 have shown some domain name or some username in common as sender of the spam but now you dont see that domain name on the server then check /var/cpanel/accounting.log to see if that account has been terminated from the server ( Ex : grep ebayspammer.com /var/cpanel/accounting.log )

All that we need to know is importance of /var/log/exim_mainlog, /var/log/formmail.log, /usr/local/apache/logs/error_log, /usr/local/apache/domlogs/*,
/var/spool/exim/input/*/* and the files uploaded in /tmp of the server. Major spamming issues are caught using the time of sending the spam. You will need to work on your own when you get across such issue and use your logic to convert the time of sending the spams to the time format of respective log files I mentioned above.


## Plesk to cPanel Account Transfer Issue

**Error 01: /scripts/packages: No such file or directory**

```
Basic credential check... Done
Account List from XX.XX.XX.X
Creating /scripts... Done
Copying pkgacct-pXa script.....0%.. ..100%.. ...Done
Copying unpkgacct script.....0%.. ..100%.. ...Done
Copying updateuserdomains-universal script.....0%.. ..100%.. ...Done
Running updateuserdomains-universal script... Done
Copying packages-pXa script......Done
Running packages script...

bash: /scripts/packages: No such file or directory


Command failed with exit status 127

Trace Output
root@XX.XXX.XX.X's password: ==sshcontroloutput== bash: /scripts/packages: No such file or directory sshcommandfailed=127


Done
Unable to run packages script
```

**Solution**:

Try running this on the Plesk box, then copy an account:

```
touch /scripts/packages
chmod 700 /scripts/packages
mkdir -p /var/cpanel/packages
echo 'FEATURELIST=unsupported' > /var/cpanel/packages/unsupported
```

Then restart the migration process. It will work fine.

**Error 02: system's version of Plesk(tm) are not supported**.

Error occurs when plesk installed on debian/ubuntu server

```
Attempting to copy ftprecetas from xx.xxx.xxx.xxx

Packaging the account: (/scripts/pkgacct ftprecetas "" --split --compressed --mysql 5.1)...
readline() on closed filehandle PSAV at /tmp/.perl-ppk-SeOGTu/scripts/main.pl line 1739.
Transfers of accounts from this system's version of Plesk(tm) are not supported. at /tmp/.perl-ppk-SeOGTu/scripts/main.pl line 77.


Command failed with exit status 1
```

**Solution**: 

cpanel migration script is checking 3 directories to get version file of plesk.


```
/usr/local/psa
/usr/local/plesk
/opt/psa
```

On debian/ubuntu the version file is in /opt/psa/version. But since cpanel script find /usr/local/psa directory so it just try to fetch plesk version from there and fails. That is a bug in their migration script

To fix it, just copy  /opt/psa/version /usr/local/psa/

```
cp /opt/psa/version /usr/local/psa/
```







