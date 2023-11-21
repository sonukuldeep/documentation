---
layout: home
title: Nested loop
parent: Php
---

## Nested loop
```php
<?php
for ($i = 0; $i < 5; $i++) {
  for ($j = 0; $j < 5; $j++) {
    echo $i . ' - ' . $j . '<br>';
  }
}

$i = 0;

while ($i < 5) {
  $j = 0;

  while ($j < 5) {
    echo $i . ' - ' . $j . '<br>';
    $j++;
  }

  $i++;
}
?>
```