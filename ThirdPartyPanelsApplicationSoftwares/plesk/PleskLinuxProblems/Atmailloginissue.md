---
title: Atmail (webmail) login issue
description: 
published: true
date: 2021-07-10T23:37:37.838Z
tags: 
editor: markdown
dateCreated: 2021-07-10T23:37:37.838Z
---

# Error With ATMail

> Error
> Warning: fopen() [function.fopen]: open_basedir restriction in effect. File(/etc/psa-webmail/atmail/.atmail.shadow) is not within the allowed path(s): (/var/www/atmail/:/var/log/atmail/:/etc/psa:/tmp/:/var/tmp/) in /var/www/atmail/libs/Atmail/Config.php on line 4
> 
> Warning: fopen(/etc/psa-webmail/atmail/.atmail.shadow) [function.fopen]: failed to open stream: Operation not permitted in /var/www/atmail/libs/Atmail/Config.php on line 4
{.is-danger}


**Solution**

For solve your problem you can edit AtMail Vost File in /etc/apache2/conf.d/zzz_atmail_vhost.conf

Open it using any editor

```
vim zzz_atmail_vhost.conf
```

delete all open_basedir configuration in this vhost and replate it to

```
php_admin_value open_basedir "/var/www/atmail:/var/log/atmail:/tmp:/var/tmp:/etc/psa-webmail/atmail"
```

Then restart apache and plesk

