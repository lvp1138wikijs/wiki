---
title: Disable SELinux on CentOS
description: 
published: true
date: 2021-12-22T14:06:36.147Z
tags: disable selinux on centos
editor: markdown
dateCreated: 2021-12-22T14:06:36.147Z
---

# Disable SELinux on CentOS
To disable SELinux, do the following steps

Login to the server via SSH

Run the following command 

>#sed -i 's/SELINUX=enforcing/SELINUX=disabled /g' /etc/selinux/config
>#reboot
