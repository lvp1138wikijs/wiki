---
title: Perl:OOPs 
description: 
published: true
date: 2021-12-20T21:00:46.062Z
tags: 
editor: markdown
dateCreated: 2021-12-20T21:00:46.062Z
---

## Methods

Methods are subroutines.

e.g Here is an example of a method or a subroutine:

```
package Forestlands;

use warnings;
use strict;

sub new {
my $class = shift;

my $self = {};
lands($self, $class);
return($self);
}

1;
```

We can use the method to create a module as shown below:

  $ perl -E 'use Forestlands; say Forestlands->new;'
  
  