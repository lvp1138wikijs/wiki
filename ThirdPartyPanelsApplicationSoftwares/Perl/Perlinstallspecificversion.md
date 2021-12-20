---
title: Perl: install specific version
description: 
published: true
date: 2021-12-20T20:58:26.589Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:58:26.589Z
---

You can install any specific version of perl since the perl versions may not be always the same in every *nix system.

```
wget http://www.cpan.org/src/5.0/perl-5.16.2.tar.gz

tar -xzf perl-5.16.2.tar.gz

cd perl-5.16.2

./Configure -des -Dprefix=$HOME/localperl

make

make test

make install
```

You can verify the new version by typing


```
$HOME/localperl/bin/perl -v

```
To make this version your default perl version add this to your .bashrc file.


```
export PATH=$HOME/localperl/bin/:$PATH
```
