---
layout: home
title: Date and date formatting
parent: Php
---

## Date and date formatting
```php
<?php
$output = null;

// Get year
$output = date('Y');

// Use a different date with a timestamp
$output = date('Y', 936345600);

// Year for a different date
$output = date('Y', strtotime('1999-09-01'));

// Get month
$output = date('m');

// Get day
$output = date('d');

// Get day of the week
$output = date('D');
$output = date('l');

// Get hour
$output = date('H');

// Get minute
$output = date('i');

// Get second
$output = date('s');

// Get AM or PM
$output = date('a');

// Get full date and time
$output = date('Y-m-d h:i:s a');

?>
```