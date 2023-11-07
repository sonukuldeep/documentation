---
layout: home
title: Php
has_children: true
---

# Php basics

## Arithmatic operations
```php
<?php
$output = null;
 
$num1 = 10;
$num2 = 20;
 
// Basic math
$output = "$num1 + $num2 = " . $num1 + $num2;
$output = "$num1 - $num2 = " . $num1 - $num2;
$output = "$num1 * $num2 = " . $num1 * $num2;
$output = "$num1 / $num2 = " . $num1 / $num2;
$output = "$num1 % $num2 = " . $num1 % $num2;
 
// Assignment operators
$num3 = 10;
 
$num3 += 10;
$num3 -= 10;
$num3 *= 2;
$num3 /= 2;
$num3 %= 2;
 
$output = $num3;
 ```
 
 ## Built in functions
 ```php
// Built in php function
 
// random numbers
$output = rand();
$output = getrandmax();
$output = rand(1, 10); // both 1 & 10 included
 
// round
$output = round(3.14);
$output = round(3.14, 1);
 
// ceil
$output = ceil(3.14); // outputs 4
 
// floor
$output = floor(3.14); // outputs 3
 
// square root
$output = sqrt(2024);
```