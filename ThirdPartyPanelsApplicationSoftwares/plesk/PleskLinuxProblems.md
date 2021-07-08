---
title: Plesk Linux Problems
description: 
published: true
date: 2021-07-08T01:30:52.804Z
tags: 
editor: markdown
dateCreated: 2021-07-08T01:30:52.804Z
---

## How to restart Plesk service from Shell

- Log-in to server shell as root user via SSH ( You can use putty from windows / In linux use console with command ssh )
- Then run the following command to restart plesk service
   - /etc/init.d/psa restart
   

## How to do auto repair on plesk databases

- Login to server via SSH as root user. 
- Then run command 

```
 mysqlcheck --all-databases -u admin -p`cat /etc/psa/.psa.shadow` --auto-repair
```

## Command to check plesk version

- Login to shell.
- Check the version file in /usr/local/psa/ there you can check the plesk version.

```
cat /usr/local/psa/version
```

## How to run statistics for a website manually

- Login to server as SSH
- The run following command. 

```
/usr/local/psa/admin/sbin/statistics -calculate-one -domain-name=_domain_name_  
 
Note: Replace _domain_name_  with your domain
```

## How do I enable remote access to MySQL database server?

To enable remote access on mysql do the following steps.

Open /etc/my.cnf and make sure that the following lines exists/commented in [mysqld] section:

```
[mysqld]
port = 3306
bind-address = 10.10.0.1
# skip-networking
....
```
- **bind-address** : local IP address to bind to. If you wish mysql listen on all IPs, don't use this option.
- **skip-networking** : Don't listen for TCP/IP connections at all. All interaction with mysqld must be made via Unix sockets. This option is highly recommended for systems where only local requests are allowed. Since you need to allow remote connection this line should be removed from file or put it in comment state.

Restart MySQL.

```
/etc/init.d/mysql restart
```

Now you should grant access to remote IP address, login to Mysql:

```
# mysql -uadmin -p`cat /etc/psa/.psa.shadow` mysql
```

For example if you want to allow access to database called 'foo' for user 'bar' and remote IP 192.168.0.1 then you need to type following commands at "mysql>" prompt:

```
mysql> GRANT ALL ON foo.* TO bar@'192.168.0.1' IDENTIFIED BY 'PASSWORD';
mysql> REVOKE GRANT OPTION ON foo.* FROM bar@'192.168.0.1';
```

## Named fails to start: bad zone

> Named service fails to start:
> 
> #/etc/init.d/psa startall
> Starting psa... done
> Starting xinetd service... done
> Starting named service... failed
> Starting mysqld service... failed
> Starting postgresql service... not installed
> Starting psa-spamassassin service... done
> Plesk: Starting Mail Server... done
> #/etc/init.d/psa reload
> Reloading SWsoft control panels server... [ OK ]
> #/etc/init.d/named reload
> Reloading named: [FAILED]
{.is-danger}


Then check the server log

```
tail /var/log/messages
...
Oct 20 13:44:32 serv1 named: zone domain.tld/IN: not loaded due to errors.
Oct 20 13:44:32 serv1 named: _default/domain.tld/IN: bad zone
Oct 20 13:44:32 serv1 named: zone domain.tld/IN: NS 'ns.domain.tld' has no address records (A or AAAA)
Oct 20 13:45:47 serv1 sw-cp-server_init: stale pidfile.
```

The issue may be caused by a corrupted Named configuration.

To fix this issue

Backup and rebuld the DNS configuration by running the below commands:

```
cd /var/named/run-root/etc
mv named.conf named.conf.bak
cp named.conf.default named.conf
for x in `ls`; do /usr/local/psa/admin/sbin/dnsmng --update $x; done;
/etc/init.d/named restart
```

