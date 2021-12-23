---
title:  Puppet Server
description: 
published: true
date: 2021-12-23T14:10:14.928Z
tags: 
editor: markdown
dateCreated: 2021-12-23T14:10:14.928Z
---

# Puppet Server

Puppet servers are used to centralize the management of linux distros running on a network.

Here are the steps to set the puppet server:

1. First make sure that you have entered the IP addresses and hostnames into the /etc/hosts file.

2. Next download the puppet server's rpm:

```
rpm -Uvh http://download.fedoraproject.org/pub/epel/5/i386/epel-release-5-4.noarch.rpm
```


3. Issue the following commands:

```
yum install puppet
yum install *puppet*
```

4. Next edit the following file:

Make the entries for the client nodes:

```
# vim /etc/puppet/manifests/site.pp
# Create “/tmp/testfile” if it doesn’t exist.
class test_class {
 file { “/tmp/testfile”:
 ensure => present,
 mode => 644,
 owner => root,
 group => root
 }
}

node puppetclient {
include test_class
}
node puppetclient {
include test_class
}
```

5. Next issue the command to start the puppet server.

```
puppet:# /etc/init.d/puppetmaster start
edit the configuration file and provide the hostname:
/etc/puppet/puppetd.conf
[puppetd]
server = "hostname"
create the log files:
logdir=/var/log/puppet
vardir=/var/lib/puppet
rundir=/var/run
```

6. Test

Verify whether the test file is created

```
# ls -l /tmp/testfile
puppetserver:# vim /etc/puppet/manifests/site.pp

class test_class {
 file { “/tmp/testfile”:
 ensure => present,
 mode => 600,
 owner => root,
 group => root
 }
}
```

7. Next tell the client on which node the class is to be run:

```
node puppetclient {
include test_class
}
```

8. Run the coommand to run the puppet client:


```
# puppetd -v -o
Next start the puppet server
puppetclient:# /etc/init.d/puppet start
```

