---
layout: home
title: String functions
parent: Php
---


## String functions
```php
$output = null;
 
$string = 'hello World';
 
// string length
$output = strlen($string);
 
// word count
$output = str_word_count($string);
 
// string position
$output = strpos($string, 'world');
 
// get specific character at index
$output = $string[4];
 
// sub string
$output = substr($string, 6, 5);
 
// replace string
$output = str_replace('world', 'hell', $string);
 
// string to lower
$output = strtolower($string);
 
// string upper
$output = strtoupper($string);
 
// uc words-- pascal case
$output = ucwords($string);
 
// trim
$output = trim('         ' . $string . '              ');
```