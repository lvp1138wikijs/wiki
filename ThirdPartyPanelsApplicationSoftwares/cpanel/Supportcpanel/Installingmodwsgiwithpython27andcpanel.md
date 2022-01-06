---
title: Installing mod_wsgi with python 2.7 and cpanel
description: 
published: true
date: 2022-01-06T02:30:50.872Z
tags: 
editor: markdown
dateCreated: 2022-01-06T02:30:50.872Z
---

# Installing mod_wsgi with python 2.7 and cpanel

First install python 2.7

```
# cd /usr/local/src/Python-2.7/
# wget http://pypi.python.org/packages/2.7/s/setuptools/setuptools-0.6c11-py2.7.egg
# sh setuptools-0.6c11-py2.7.egg --prefix=/usr/local/python27
```

```
# cd /usr/local/python27/bin
# ./easy_install virtualenv
# ./easy_install django
# cd /usr/local/python27/lib/python2.7/config/
# ln -s ../../libpython2.7.so
```

```
# cd /usr/local/src/Python-2.7/
# wget https://modwsgi.googlecode.com/files/mod_wsgi-3.4.tar.gz
# tar xzvf mod_wsgi-3.4.tar.gz
# cd mod_wsgi-3.4
# ./configure --with-python=/usr/local/python27/bin/python --enable-shared
# make && make install
```

We need to avoid cPanel's easy_apache clearing up /usr/local/apache/modules folder

```
# mkdir /usr/local/apache/extramodules
# mv /usr/local/apache/modules/mod_wsgi.so /usr/local/apache/extramodules/
```

Include mod_wsgi into Apache configuration

```
# nano /usr/local/apache/conf/includes/pre_virtualhost_global.conf
```

paste:

```
LoadModule wsgi_module /usr/local/apache/extramodules/mod_wsgi.so
AddHandler wsgi-script .wsgi
```

Before we restart Apache, lets test if we have the correct configuration

```
# service httpd configtest
```

You should get this answer:

```
Syntax OK
```

Now restart Apache

```
# /scripts/restartsrv httpd
```

You can create a test.wsgi file to test Python scripts with following code

```

def application(environ, start_response):
    """Simplest possible application object"""
    output = "Hello World"
    status = '200 OK'
    response_headers = [('Content-type', 'text/plain'),
                        ('Content-Length', str(len(output)))]
    start_response(status, response_headers)
    return [output]
```

