---
layout: home
title: Associative array
parent: Php
---

## Associative array
```php
<?php
$output = null;
$user = [
    'name' => 'John',
    'email' => 'john@gmail.com',
    'passwd' => '123456',
    'hobbies' => ['Tennis', 'video games']
];
 
$output = $user['name'];
$output = $user['email'];
$output = $user['hobbies'][0];
 
$user['address'] = '123 Main St';
 
unset($user['address']);
 
?>
```