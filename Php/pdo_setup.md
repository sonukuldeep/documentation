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

## Fetch multiple
```php
Fetch/get multiple

<?php
require "pdo.php";
 
// Prepare a select statement
$stmt = $pdo->prepare('SELECT * FROM posts');
 
// Execute the statement
$stmt->execute();
 
// Fetch results
$posts = $stmt->fetchAll();
 
echo '<pre>';
var_dump($results);
echo '</pre>';
?>
```

## Fetch single
```php
<?php
require "pdo.php";
 
$id = $_GET['id'] ?? null;
 
if (!$id) {
  header('location: index.php');
  exit;
}
 
$sql = 'SELECT * FROM posts WHERE id = :id';
 
$stmt = $pdo->prepare($sql);
 
$params = ['id' => $id];
 
$stmt->execute($params);
 
$post = $stmt->fetch();
 
?>
```

## Create new
```php

<?php
require "pdo.php";
 
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['submit'])) {
  $title = htmlspecialchars($_POST['title']);
  $body = htmlspecialchars($_POST['body']);
 
  $sql = 'INSERT INTO posts(title, body) VALUES (:title, :body)';
 
  $stmt = $pdo->prepare($sql);
 
  $params = [
    'title' => $title,
    'body' => $body
  ];
 
  $stmt->execute($params);
 
  header('location: index.php');
}
 
?>
```

## Delete
```php
<?php
require "pdo.php";
 
$isDeleteRequest = $_SERVER['REQUEST_METHOD'] === 'POST' && ($_POST['_method'] ?? '' === 'delete');
 
if ($isDeleteRequest) {
    $id = $_POST['id'];
 
    $sql = 'DELETE FROM posts WHERE id = :id';
 
    $stmt = $pdo->prepare($sql);
 
    $params = ['id' => $id];
 
    $stmt->execute($params);
 
    header('location: index.php');
    exit;
}
?>

<form action="delete.php" method="post">
    <input type="hidden" name="_method" value="delete">
    <input type="hidden" name="id" value="<?= $post['id'] ?>">
    <button type="submit" name="submit" class="bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600 focus:outline-none">Delete</button>
</form>
```