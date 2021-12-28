---
title: LAMP on CentOS6
description: 
published: true
date: 2021-12-28T14:02:32.996Z
tags: lamp
editor: markdown
dateCreated: 2021-12-28T14:02:32.996Z
---

# LAMP on CentOS6

### *Copy paste below commands*

> wget https://fedoraproject.org/static/0608B895.txt
> mv 0608B895.txt /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
> rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6
> rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
> yum install httpd php php-cli mod_fcgid php-cgi php-mysql php-common php-gd php-mcrypt php-imap php-ldap php-odbc php-xmlrpc  php-curl perl* unzip mysql-server
> service httpd start
> service mysqld start
> chkconfig httpd on
> chkconfig mysqld on
> rm -rf /var/www
> mkdir -p /var/www/cgi-bin
> groupadd serverp
> useradd -s /bin/false -d /var/www -m -g serverp serverp
> chown -R serverp:serverp /var/www
> sed -i 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=1/g' /etc/php.ini
> cat >> /var/www/cgi-bin/php.fcgi <<END
> #!/bin/bash
> PHP_CGI=/usr/bin/php-cgi
> PHP_FCGI_CHILDREN=4
> PHP_FCGI_MAX_REQUESTS=0
> export PHP_FCGI_CHILDREN
> export PHP_FCGI_MAX_REQUESTS
> exec PHP_CGI
> END
>  
> sed -i 's/exec PHP_CGI/exec $PHP_CGI/g' /var/www/cgi-bin/php.fcgi
> chmod 755 /var/www/cgi-bin/php.fcgi
> chown -R serverp:serverp /var/www/cgi-bin/php.fcgi
> cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.`date +%Y-%m-%d:%H:%M:%S`
> sed -i 's/expose_php = On/expose_php = Off/g' /etc/php.ini
> sed -i 's/allow_url_fopen = On/allow_url_fopen = Off/g' /etc/php.ini
> sed -i 's/ServerTokens OS/ServerTokens Prod/g' /etc/httpd/conf/httpd.conf
> sed -i 's/ServerSignature On/ServerSignature Off/g' /etc/httpd/conf/httpd.conf
>  
> cat >> /etc/httpd/conf.d/fcgid.conf <<END
> FcgidConnectTimeout 200
> FcgidMaxRequestLen 15728640
> FcgidFixPathinfo 1
> END
>  
> cat >> /etc/httpd/conf/httpd.conf <<END
> <VirtualHost *:80>
>     ServerAdmin webmaster@localhost
>     DocumentRoot /var/www
>     DirectoryIndex index.html index.htm index.php index.phtml index.php5 default.html default.php default.phtml default.php5
>     SuexecUserGroup serverp serverp
>     <Directory /var/www>
>         Options FollowSymLinks MultiViews +ExecCGI
>         AllowOverride All
>         AddHandler php5-fastcgi .php .phtml .php5
>         Action php5-fastcgi /cgi-bin/php.fcgi
>         Order allow,deny
>         allow from all
>     </Directory>
>     ScriptAlias /cgi-bin/ /var/www/cgi-bin/
>     <Directory "/var/www/cgi-bin">
>         AllowOverride All
>         Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
>         Order allow,deny
>         Allow from all
>     </Directory>
>     ErrorLog /var/log/httpd/default.error.log
>     # Possible values include: debug, info, notice, warn, error, crit,
>     # alert, emerg.
>     LogLevel warn
>     CustomLog /var/log/httpd/default.access.log combined
> </VirtualHost>
> END
>  
> service httpd restart
>   