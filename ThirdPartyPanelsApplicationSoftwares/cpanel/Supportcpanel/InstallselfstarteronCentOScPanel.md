---
title: Install selfstarter on CentOS / cPanel
description: 
published: true
date: 2022-01-06T05:05:39.557Z
tags: 
editor: markdown
dateCreated: 2022-01-06T05:05:39.557Z
---

# Install selfstarter on CentOS / cPanel

The selfstarter script is written in Ruby, and its latest version requires Ruby 1.9.2 or later.For the latest version available to close, it requires Ruby 1.9.3.

Since cPanel doesn't support Ruby 1.9.x by default, we have to install it via RVM to the particular users home directory. In order to install Ruby 1.9.3 , please do the following steps:

1.Make sure the following packages are installed on the server. If not, install them as root user.

```
gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison iconv-devel
```

2.For installing  EPEL repository, please click here .

3.Install npm package from EPEL repository. When done disable the EPEL repository to avoid any future package conflicts.

```
yum --enablerepo=epel install  npm
```

4.Now "su" to the target user ( cPanel user under which we should install the application )

```
su - user
```

5.Make sure we are in the home directory of target user.

```
cd~
```
6.Now run the following command to install and load RVM.

```
bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)
 source "$HOME/.rvm/scripts/rvm"
```

7.Configure Bash to load RVM automatically at login.

```
echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc
```

8.Now install ruby and make it default for the target user

```
rvm install 1.9.3
 rvm --default 1.9.3
```

9.Now run the following commands to install selfstarter from target user's shell:

```
git clone https://github.com/lockitron/selfstarter.git
 cd selfstarter
 bundle install --without production
 rake db:migrate
 rake db:seed
```

10.To run selfstarter, run the following command:

```
rails s
```

11.Now selfstarter should be listening on port 3000 and you can access it using URL http://ServerIP:3000

URL referred: https://github.com/lockitron/selfstarter
                      http://davejamesmiller.com/blog/installing-rails-3-1-ruby-1-9-on-a-cpanel-11-30-server


The selfstarter script is written in Ruby, and its latest version requires Ruby 1.9.2 or later.
 



