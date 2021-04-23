---
title: Install SitemapXML in zencart
description: 
published: true
date: 2021-04-23T17:37:06.981Z
tags: 
editor: markdown
dateCreated: 2021-04-23T17:37:06.981Z
---

BACK UP your database & store.

 1. Unzip the SitemapXML package to your local hard drive, retaining the folder structure.

 2. Rename the "YOUR_Admin" folder in the "sitemapXML" folder to match the name of your admin folder.

     sitemapXML/YOUR_Admin/

 3. Upload the files from "sitemapXML" to the root of your store. (DO NOT upload the "sitemapXML" folder, just the CONTENTS of this folder

   (copy ALL of the add-on files to your store!! Most issues are caused by store owners who decide to NOT load ALL of the module files)

4. Set permissions on the directory /sitemap/ to 777.

5.1. If your are running Zen-Cart 1.5.x. Run install-sitemapxml_only_for_zen-cart-1_5_0.sql (If you are running Zen Cart 1.3.9, SKIP THIS STEP!)

 Goto Admin - Tools - Install SQL Patches

Copy and paste content of the install-sitemapxml_only_for_zen-cart-1_5_0.sql and click Send. to run install-sitemapxml_only_for_zen-cart-1_5_0.sql

6. Go to Admin -> Tools -> Sitemap XML and click "Install SitemapXML SQL".

** Reference Ticket ID : SGB-725-54976**