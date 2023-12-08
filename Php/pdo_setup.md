---
layout: home
title: Pdo
parent: Php
---

```php
<?php
// php data object

//  database creds
$host = 'localhost';
$port = 3306;
$dbName = 'blog';
$username = 'sonu';
$password = 'sonu';

$dsn = "mysql:host={$host};port={$port};dbname={$dbName};charset=utf8";
try {
    // create pdo instance
    $pdo = new PDO($dsn, $username, $password);

    // set pdo to throw exceptions on error
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    // fetch as assoc array
    $pdo->setAttribute(PDO::ATTR_DEFAULT_FETCH_MODE, PDO::FETCH_ASSOC);
} catch (PDOException $e) {
    echo 'connection failed' . $e->getMessage();
}
```