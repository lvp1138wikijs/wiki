---
title: Exim Spam tracing
description: 
published: true
date: 2022-01-23T06:08:44.916Z
tags: 
editor: markdown
dateCreated: 2022-01-23T06:08:44.916Z
---

# Exim Spam tracing

1. To check the number of emails present in the queue:

#exim -bpc

2. To check the emails present in the queue with the mail id and sender
ID:

#exim -bp

#exim -bp | less

3. To view the header of a particular email using mail ID:

#q mail_id

4. To view the body of a particular email using mail ID:

#exim -Mvb mail_id

5. To view a message's logs:

#exim -Mvl mail_id

6. To trace path:

#exim -d -bt user@domain.com

7. To get sorted list of email sender in exim queue:

#exim -bpr | grep "<" | awk {'print $4'} |cut -d "<" -f 2 | cut -d ">"
-f 1 | sort -n | uniq -c| sort -n

8. To check the script that will originate spam mails:

#grep "cwd=" /var/log/exim_mainlog|awk '{for(i=1;i<=10;i++){print$i}}'|sort| uniq -c|grep cwd|sort -n

9. If we need to find out exact spamming script. To do this, run
following command:

#ps auxwwwe | grep user | grep --color=always"/home/user/public_html/templates/" | head

10. To delete the emails of a specific user:

#grep -lr 'user@domain.com' /var/spool/exim/input/ | sed -e
's/^.*\/\([a-zA-Z0-9-]*\)-[DH]$/\1/g' | xargs exim -Mrm

#exim -bp | grep "user_email-account" | awk '{print $3}' | xargs exim
-Mrm

11. To delete Frozen emails from the email queue:

#grep -R -l '*** Frozen' /var/spool/exim/msglog/*|cut -b26-|xargs exim
-Mrm

#exim -bp| grep frozen | awk '{print $3}'| xargs exim -Mrm

#exiqgrep -z -i | xargs exim -Mrm

12. To delete Spam emails from the email queue:

#grep -R -l [SPAM] /var/spool/exim/msglog/*|cut -b26-|xargs exim -Mrm

13. To check the no. of frozen mails:

#exiqgrep -z -c

14. To check exim logs:

#tail -f /var/log/exim_mainlog

15. Force delivery of one message:

#exim -M mail_id

16. Force another queue run:

#exim -qf

17. Force another queue run and attempt to flush frozen messages:

#exim -qff

18. To check if there are frozen emails:

#exim -bp |awk '/fr[o]zen/ {print}'

19. To clear just one email:

#exim -Mrm mail_id

20. Check the subjects of the emails:

#exiqgrep -i |awk '{ print "exim -Mvh "$1 }' |sh |grep -i Subject