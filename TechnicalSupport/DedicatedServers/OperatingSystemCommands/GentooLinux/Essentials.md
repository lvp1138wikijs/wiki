---
title: Gentoo Linux Essentials
description: 
published: true
date: 2021-12-30T14:09:58.613Z
tags: gentoo linux
editor: markdown
dateCreated: 2021-12-30T14:09:58.613Z
---

# Gentoo Linux

#### Location of common configuration files


#### Typical configuration example

#### Network config
/etc/conf.d/net

#### Typical configuration example

routes_eth0=( "default via 72.18.198.1" )
config_eth0=( 72.18.198.4/24 )

Details:
 - “default via”: refers to the gateway

#### Local startup

/etc/conf.d/local.start

Any commands placed in this file will be automatically executed after the operating system's startup phase. Make sure to use & at the end of commands, or else the boot process will not complete if a command does not properly exit.


#### Local shutdown

/etc/conf.d/local.stop

Any commands placed in this file will be executed before the shut down phase


#### Startup files

/etc/init.d

## Package Maintenance Procedures

	In Gentoo, the command to do upgrades, remove packages and install is emerge. This is part of Gentoo's Portage, the system to maintain installed packages.


#### How to configure this command to download from mirrors

By default, emerge is already configured to search for a mirror, unlike yum and apt-get which require such configurations.

#### How to install

emerge package_name



#### Upgrade procedure

emerge -u package_name

Dependencies: emerge will automatically install dependencies


#### Removal procedure

emerge --unmerge package_name

Dependencies: emerge will warn about any other packages that depend on this package, or, packages that need to also be removed. Be very careful. It's better to just not remove packages in gentoo.

#### Search if a package is installed

emerge -s name

Or, go to emerge's library directory. See below.



- Where does this command store information about what's installed and available packages

/usr/portage

 - There, you will see directories and sub directories of all the packages available for installation. For example:


/usr/portage/dev-php5/jpgraph

 - If you wish to install such a package:

emerge -u dev-php5/jpgraph

- You can also do:

emerge -u jpgraph

	However, emerge may sometimes not find the package. Or, various packages may have similar names. We recommend that you use the -u parameter so that if the package is already installed, it will check if there is an upgrade. If not, then emerge will not do anything. If you omit the -u parameter, emerge will reinstall the package. Sometimes it's useful to recompile a package, specially those related to SSL. 




#### Global upgrade

Before upgrading Gentoo, you must first synch /usr/portage with the public Portage directory. You do this with:


	emerge --sync

To upgrade all packages in the system:

	emerge -u world --deep

We recommend however that you first do:

	emerge -u world --deep --pretend
  
  This will tell you which packages are to be installed, and if there are any conflicting packages. Problems may arise due to that however. See below.

#### Kernel Upgrade

**Problems**


 - SSL issues - packages that depend on SSL, sometimes, require openssl to be recompiled
 - Conflicting packages
