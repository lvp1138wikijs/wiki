---
title:  Change of user for shared hosting account 
description: 
published: true
date: 2021-03-26T12:10:19.742Z
tags: 
editor: markdown
dateCreated: 2021-03-26T12:10:19.742Z
---

# Change of user for shared hosting account
> update userdata set username = "_new-username_" where username = "_old-username_" and account_type != "dedicolo";
> update userdata_customer set username = "_new-username_" where username = "_old-username_";
> update sharedtrack set username = "_new-username_" where username = "_old-username_";
> update sharedtrack_sites set sc_username = "_new-username_" where sc_username = "_old-username_";
> update mysql_users set username = "_new-username_" where username = "_old-username_";
> delete from userdata_ccard where username = "_old-username_";
{.is-info}

**Replace**
-     _new-username_ with new username
-     _old-username_ with old username

These queries will require:
- that the new username provides credit card information

- the the old username provides personal contact information
    
    
    
    