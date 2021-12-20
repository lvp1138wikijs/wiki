---
title: Loops 
description: 
published: true
date: 2021-12-20T20:53:30.258Z
tags: 
editor: markdown
dateCreated: 2021-12-20T20:53:30.258Z
---

# Loops 


## For

The syntax for the for loop is as follows:

```
LABEL for (exp; exp; exp) BLOCK
```

e.g.,

 
for ($i=0;$i<10;$i++)
{
print $1*$i;
print "\n";

}

## Foreach

syntax:

```
foreach (@array)
{
   print "$_\n";
}
```

## Until

The syntax for the until loop is:

 
```
do 

BLOCK

until(exp);
```

## While

Here is the syntax for the while loop:

```
while explabel
while (exp) BLOCKLABEL
while (exp) BLOCK continue BLOCK
```
