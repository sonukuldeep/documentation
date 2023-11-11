---
layout: home
title: Array basics
parent: Php
---

## Array basics
```php
<?php

$names = array('John', 'Jack', 'Jill');
$numbers = [1, 2, 3, 4, 5, 6];

function inspect($value)
{
  echo '<pre>';
  var_dump($value);
  echo '</pre>';
}

// inspect($names);
// inspect($numbers);

// print_r($names);

// echo $names[2];
// echo $numbers[3];

// Add element to array
$numbers[] = 100;
$numbers[] = 101;

$numbers[3] = 200;

// leaves a whole in array
unset($numbers[3]);

// reorders/add missing index 
$numbers = array_values($numbers);

inspect($numbers);

```