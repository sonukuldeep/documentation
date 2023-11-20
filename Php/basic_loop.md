---
layout: home
title: Basic loop
parent: Php
---

## Basic loop
```php
<?php
$output = null;

// Simple for loop
for ($i = 0; $i <= 10; $i++) {
    echo $i; 
}

// Simple while loop
$i = 0;
while ($i < 10) {
    echo $i; 
    $i++;
}

// Simple do...while loop
$i = 0;

do {
    echo $i; 
    $i++;
} while ($i < 10);
?>
```

### Loop within html

#### For loop
```php
    <ul>
    <?php for ($i = 0; $i <= 10; $i++) : ?>
        <li>Number <?= $i ?></li>
        <?php endfor; ?>
    </ul>
```

#### While loop
```php
<ul>
    <?php $counter = 1; while ($counter <= 5) : ?>
        <li>Item <?= $counter ?></li>
    <?php $counter++; endwhile ?>
</ul>
```