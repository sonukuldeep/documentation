---
layout: home
title: Environment variables
parent: Php
---

## Environment variables
```php
// var_dump(getenv())
 
putenv('DB_HOST=localhost');
putenv('DB_USER=root');
 
$host = getenv('DB_HOST');
$user = getenv('DB_USER');
```