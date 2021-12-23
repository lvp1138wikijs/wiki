---
title: Traccar
description: 
published: true
date: 2021-12-23T18:08:03.184Z
tags: 
editor: markdown
dateCreated: 2021-12-23T18:07:35.099Z
---

# Traccar

Traccar: GPS Tracking Software - Free and Open Source System
https://www.traccar.org/
Traccar is the leading GPS tracking software. Vehicle and personal tracking. Self hosting and cloud-based solution. Real time view, reports, notifications

## Installation - Traccar

This is tutorial will explain how to install and configure Traccar application on CentOS 7 VPS. 

1. **Install and Configure Java**

Install Java using Yum

```
yum update -y
yum install java -y
```

Run java update alternative command to get the config path

```
update-alternatives --config java
-----------------------------------------------
*+ 1 java-1.8.0-openjdk.x86_64 (/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/jre/bin/java)
```

Set environment value for Java Home

```
cat >> /etc/environment <<END
JAVA_HOME="/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/"
END
source /etc/environment
```
Test it by running echo command

```
echo $JAVA_HOME
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/
```

2. **Traccar Installation**

Download the Traccar

```
cd /usr/local/src
wget  https://github.com/tananaev/traccar/releases/download/v3.15/traccar-linux-3.15.zip
```

Extract and install Traccar

```
unzip traccar-linux-3.15.zip
rm -rf traccar-linux-3.15.zip
./traccar.run
```

It will install the application on location /opt/traccar 

Start Traccar

Run any of the following commands

```
/etc/init.d/traccar start
service traccar start
/opt/traccar/bin/startDaemon.sh
```

Default http port is used by the application is 8082. Now we can access the application on - http://ipaddress:8082/

Default username and password is  admin / admin

```
Note: replace ipaddress with the server public IP address
```

3. **Install and configure Apache**

Install Apache using Yum

```
yum install httpd  mod_ssl openssl -y
```

configure Traccar on apache with SSL

```
Notes:
Replace your_domain.com with your domain name
Put the SSL cert, key and CA to the location /etc/httpd/ssl and correct the names
```

Go to /etc/httpd/conf.d  and create new configuration file traccar.conf with following 

```
cat >> /etc/httpd/conf.d/traccar.conf <<END
<VirtualHost *:80>
 ServerName your_domain.com
 DocumentRoot /opt
ProxyRequests off
ProxyPass /api/socket ws://127.0.0.1:8082/api/socket
 ProxyPassReverse /api/socket ws://127.0.0.1:8082/api/socket
ProxyPass / http://127.0.0.1:8082/
 ProxyPassReverse / http:/127.0.0.1:8082/
</VirtualHost>
<VirtualHost *:443>
 ServerName your_domain.com
 DocumentRoot /opt
SSLEngine on
 SSLCertificateFile /etc/httpd/ssl/your_domain.crt
 SSLCertificateKeyFile /etc/httpd/ssl/your_domain.key
 SSLCertificateChainFile /etc/httpd/ssl/your_domainCA.crt
ProxyRequests off
ProxyPass /api/socket ws://127.0.0.1:8082/api/socket
 ProxyPassReverse /api/socket ws://127.0.0.1:8082/api/socket
ProxyPass / http://127.0.0.1:8082/
 ProxyPassReverse / http:/127.0.0.1:8082/
</VirtualHost>
END
```

Then restart traccar and apache service

```
service traccar restart
service httpd restart
```

Now you can access the Traccar interface through  http://your_domain.com and https://your_domain.com 

No need to specify the port 8082.

4. **Install MySQL and configure Traccar with MySQL**

Install MySQL 

```
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
rpm -ivh mysql-community-release-el7-5.noarch.rpm
yum update -y
yum install mysql mysql-server
systemctl enable mysqld
systemctl start mysqld
```

Set MySQL root user password and other settings by running command

```
mysql_secure_installation
```

Now login to MySQL as root

```
mysql -u root -p
```

Run the following MySQL queries to create database traccar, database user traccar, and its password

```
create database traccar;
grant all on traccar.* to traccar@'localhost' identified by 'pwtraccar' with grant option; 
grant all on traccar.* to traccar@'%' identified by 'pwtraccar' with grant option;
flush privileges;
```

Stop the Traccar Daemon

```
service traccar stop or sh /opt/traccar/bin/stopDaemon.sh
```

Update the conf file of Traccar

```
vi /opt/traccar/conf/traccar.xml
```
Default We will find the following datasource for h2 database, we will have to comment that datasource entry.

```
<!--
 <entry key='database.driver'>org.h2.Driver</entry>
 <entry key='database.url'>jdbc:h2:./data/database</entry>
 <entry key='database.user'>sa</entry>
 <entry key='database.password'></entry>
-->
```

Now we will add the datasource entry for the mysql database. 

```
<entry key='database.driver'>com.mysql.jdbc.Driver</entry> 
<entry key='database.url'>jdbc:mysql://localhost:3306/traccar?useSSL=false&amp;allowMultiQueries=true&amp;autoReconnect=true&amp;useUnicode=yes&amp;characterEncoding=UTF-8&amp;sessionVariables=sql_mode=''</entry>
<entry key='database.user'>traccar</entry> 
<entry key='database.password'>pwtraccar</entry>
```

Save the traccar.xml. Then start the traccar daemon

```
service traccar start  or sh /opt/traccar/bin/startDaemon.sh
```

It will take some more time, as traccar will create the tables and all necessary details to that data. you can monitor it using

```
tail -f /opt/traccar/logs/wrapper.log.DATE
```

Finally, you will see a started message

```
FINEST|2888/0|Service traccar|18-02-28 13:29:28|[main] INFO org.eclipse.jetty.server.handler.ContextHandler - Started o.t.w.@1859ffda{/,null,AVAILABLE}
FINEST|2888/0|Service traccar|18-02-28 13:29:28|[main] INFO org.eclipse.jetty.server.ServerConnector - Started ServerConnector@61cda923{HTTP/1.1}{0.0.0.0:8082}
FINEST|2888/0|Service traccar|18-02-28 13:29:28|[main] INFO org.eclipse.jetty.server.Server - Started @193064ms
```

Done






