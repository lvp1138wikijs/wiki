---
title: Ruby on Rails
description: 
published: true
date: 2021-12-23T14:16:51.887Z
tags: 
editor: markdown
dateCreated: 2021-12-23T14:11:45.318Z
---

# Ruby on Rails

ROR or Ruby on Rails is an open source web framework.

ROR is an object oriented language.


## Preinstalled gems


The gems in Ruby are a package utility that installs the  Ruby software package. Rubygems keep Ruby up-to-date.

The following are  the list of the pre-installed RubyGems:

- activerecord (1.14.2) - Implements the ActiveRecord pattern for ORM
- gruff (0.1.2) - A library for making graphs
- mysql (2.7) - The MySQL Ruby gem allows you to connect to and use MySQL databases. We fully support MySQL and the Ruby bindings to it.
- rails (1.1.2) - The Ruby on Rails package
- rake (0.7.1) - Ruby based make-like utility, required by many Ruby applications and gems.
- rmagick (1.10.1) - RMagick allows you to use the ImageMagick and GraphicsMagick libraries, similar to GD support in PHP or Perl.
- sources (0.0.1) - This package provides download sources for remote gem installation
- activesupport (1.3.1) - Support and utility classes used by the Rails framework
- fcgi (0.8.6.1) - The fcgi gem facilitates FastCGI, which we use in concert with mod_fastcgi to accelerate your Ruby on Rails applications
- actionmailer (1.2.1) - Service layer for easy email delivery and testing
- actionpack (1.12.1) - Web-flow and rendering framework putting the VC in MVC
- actionwebservice (1.1.2) - Web service support for Action Pack


## ROR:installation

Follow these steps to install ROR in your server:

- Select and go to any directory where you  will install ROR:

```
    cd /
    mkdir temp
    chmod 775 temp
```

- Next download ROR from it's source on the internet.
- The following link has the source code fro all the Operating systemas and distros:

http://rubyforge.org/frs/?group_id=167

```
cd temp
wget ftp://ftp.ruby-lang.org/pub/ruby/ruby-1.8.2.tar.gz
tar -zxvf ruby-1.8.2.tar.gz cd ruby-1.8.2
```

- We can next isnatll ROR in the /usr/local/ruby direcory:

```
./configure -prefix=/usr/local/ruby -exec-prefix=/usr/local/ruby
```

- Next move on to the compilation of the source code:

```
make
make install
```

Now you have installed ROR in your linux server.





