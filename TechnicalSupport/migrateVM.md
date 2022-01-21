---
title:  Migrate colossuscloud VM from one Zone to another. 
description: 
published: true
date: 2022-01-21T12:53:31.070Z
tags: 
editor: markdown
dateCreated: 2022-01-21T12:53:31.070Z
---

#  Migrate colossuscloud VM from one Zone to another. 

The below steps explains ,how we can change the vm zone.

For example to move the vm from zone ASH1- AMS (Amsterdam)
Step-by-step guide

    Login to Client Portal->Menu->ColossusCloud Manager

    Click on VM ->"Actions" tab above and choose the "Save VM" option

    Then create a new vm in "AMS" zone with the same configuration using that snapshot as template.
    Once new vm is up and working fine you can delete old vm.
