---
title: Installing Ruby On Rails (For cPanel)
description: 
published: true
date: 2022-01-06T02:33:04.299Z
tags: 
editor: markdown
dateCreated: 2022-01-06T02:33:04.299Z
---

# Installing Ruby On Rails (For cPanel)


## Installing Ruby On Rails


Installing Ruby on Rails is very easy on cpanel, it can be installed using one simple command

```
# /scripts/installruby
```

It will take 10-15min to complete installation, once installation will complete and you will get prompt again then you can run following command to start ruby on rail service.

```
# /usr/local/cpanel/bin/ror_setup
```

**Basic Rails Troubleshooting**

Since Ruby on Rails uses it's own web server, it has to run this web server on an alternate port and this causes an issue if you are running a firewall on your system. You will need to ensure that port 12001 and up are open (we recommend making the max number of the open ports 12001+ whatever the number of Ruby applications you expect to be running will be).

Sometimes the gems repos will go down, if this happens during the installation you will need to re-run /scripts/installruby

Source: http://www.cpanel.net/docs/ror/index.html

