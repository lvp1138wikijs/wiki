---
title: Perl function: Split
description: 
published: true
date: 2021-12-20T20:56:20.544Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:56:20.544Z
---

Perl's split function can be used to convert a string into an array.


```
$data1= "Ron:Mathew:Singer:26:Wood Chase";
@employee= split(/:/, $info);
```
The above commands result in the below array:


```
@employee= ("Ron", "Mathew", "Singer", "26", "Wood Chase");

```

