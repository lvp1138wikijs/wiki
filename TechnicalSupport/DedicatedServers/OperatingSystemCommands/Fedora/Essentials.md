---
title: Essentials in Fedora
description: 
published: true
date: 2021-12-29T12:33:53.249Z
tags: essentials in fedora
editor: markdown
dateCreated: 2021-12-29T12:33:53.249Z
---

# Fedora

### Drive label
From Fedora core 7, FC8 and FC9, FC10 all use drive labels to recongnize the drive. If Fedora is not booting then you have to check either the correct labels are assgined to the the drives in /boot/grub/grub.conf and /etc/fstab or not.

- Open the /boot/grub/grub.conf.

`vi /boot/grub/grub.conf`

- it should have following in the kernal line.

> root=LABEL=/
>  
> If it have,
> root=/dev/hda1 or root=/dev/sda1
> then correct it as above.
> 
{.is-info}

- Open /etc/fstab.

> vi /etc/fstab
{.is-info}

 - it should have lines as below.
 
>  LABEL=/
> LABEL=/boot
> LABEL=swap
> Instead of
> /dev/hda1
> /dev/hda2
> /dev/hda3
{.is-info}



