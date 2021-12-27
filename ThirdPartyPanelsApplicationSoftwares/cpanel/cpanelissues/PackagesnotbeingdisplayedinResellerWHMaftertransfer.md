---
title: Packages not being displayed in Reseller WHM after transfer
description: 
published: true
date: 2021-12-27T15:53:32.903Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:53:32.903Z
---

# Packages not being displayed in Reseller WHM after transfer


Sometimes packages will not be displayed in Reseller WHM >> Packages >> Edit, Delete lists after transfer. The issue occurs when some packages are transferred with the accounts from dedicated servers, VPS etc to Shared/Reseller servers. In order to fix this issue, please do the following steps:

1. Check if the packages are displayed under Create Account option in Reseller WHM.

2, If so check the package names : they should be prefixed with its owner name 'user_'(Reseller account name).

3. If the username prefix is missing, it will not be available for editing or deleting in reseller WHM.

E.g: For a package 'testpack' under the reseller 'new'.

The package name should be displayed as 'new_testpack'.

4. If not, rename the package from the command line, prefixed with corresponding usernames.

mv /var/cpanel/packages/testpack  /var/cpanel/packages/new_testpack

Then the package will become available for editing and deleting in Reseller WHM. After this, all the accounts under the modified packages or plans should be updated with the new package name.