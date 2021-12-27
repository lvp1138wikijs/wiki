---
title: RVSkin Error while accessing the Cpanel
description: 
published: true
date: 2021-12-27T16:09:17.350Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:09:17.350Z
---

# RVSkin Error while accessing the Cpanel


If you are getting the following error while accessing the cpanel using rvskin;

```
[a fatal error or timeout occurred while processing this directive]

Can’t locate lib.pm in @INC (@INC contains: /usr/local/cpanel /usr/local/cpanel/perl /usr/local/cpanel/Cpanel/CPAN/overload/__Digest /usr/local/cpanel/build-tools/stubs /usr/lib/perl5/5.6.2/i686-linux /usr/lib/perl5/5.6.2 /usr/lib/perl5/site_perl/5.6.2/i686-linux /usr/lib/perl5/site_perl/5.6.2 /usr/lib/perl5/site_perl .) at /usr/local/cpanel/Cpanel/Rvskin.pm line 48. BEGIN failed–compilation aborted at /usr/local/cpanel/Cpanel/Rvskin.pm line 48. require Cpanel/Rvskin.pm called at (eval 8) line 1 main::BEGIN() called at /usr/local/cpanel/Cpanel/Rvskin.pm line 48 eval {…} called at /usr/local/cpanel/Cpanel/Rvskin.pm line 48 eval ‘use Cpanel::Rvskin ();’ called at cpanel.pl line 4954 main::modloader(’Rvskin’) called at /usr/local/cpanel/Cpanel.pm line 209 Cpanel::loadmodule(’Rvskin’) called at cpanel.pl line 1631
```

Please follow the steps given below to fix it.

1) Check whether the perl version has upgraded to the latest version 5.8.8. If not, you need to update it.

```
# wget http://layer1.cpanel.net/perl588installer.tar.gz
# tar -vzxf perl588installer.tar.gz
# cd perl588installer
# ./install
```

2) Also update all the perl modules using the commands

```
/usr/local/cpanel/bin/checkperlmodules

/usr/local/cpanel/startup
```

3) Now locate the correct path of the perl module 'lib.pm'. Then you have  to give the required symbolic link for the perl module to /usr/local/cpanel/perl :

```
ln -s /usr/lib/perl5/5.8.8/i686-linux/lib.pm /usr/local/cpanel/perl
```

4) Now update rvskin to resolve the issue.

```
wget  http://member.rvskin.com/auto_rvskin.tgz
tar -xvzf auto_rvskin.tgz;
perl  auto_rvskin.pl
```

This should fix the issue. Try access Cpanel again :)

