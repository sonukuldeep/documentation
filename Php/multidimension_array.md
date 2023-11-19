---
layout: home
title: Multi dimensional array
parent: Php
---

```php
<?php
$output = null;
$fruit = [
    ["banana", "apple"],
    ["grapes", "vine"],
    ["pamagranade", "cucumber"],
];
 
$fruit[] = ["orange", "pea"];
 
$users = [
    ['name' => 'mike', 'email' => 'mike@gmail.com', 'password' => 123456],
    ['name' => 'john', 'email' => 'john@gmail.com', 'password' => 123456],
    ['name' => 'sofie', 'email' => 'sofie@gmail.com', 'password' => 123456],
];
 
$users[] = ['name' => 'peter', 'email' => 'peter@gmail.com', 'password' => 123456];
 
$output = $users[3]['name'];
 
array_pop($users);
 
array_push($users, ['name' => 'spongebob', 'email' => 'squarepants@gmail.com', 'password' => 123456]);
 
unset($users[2]);
 
?>
```