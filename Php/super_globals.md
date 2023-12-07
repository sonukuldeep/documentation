---
layout: home
title: Super globals
parent: Php
---


## Super globals
```php
<?php
// Common server variables:
// $requestMethod = isset($_SERVER['REQUEST_METHOD']) ? $_SERVER['REQUEST_METHOD'] : '';
$requestMethod = $_SERVER['REQUEST_METHOD'] ?? '';
$serverProtocol = $_SERVER['SERVER_PROTOCOL'] ?? '';
$serverName = $_SERVER['SERVER_NAME'] ?? '';
$serverPort = $_SERVER['SERVER_PORT'] ?? '';
$serverSoftware = $_SERVER['SERVER_SOFTWARE'] ?? '';
$serverAdmin = $_SERVER['SERVER_ADMIN'] ?? '';
$documentRoot = $_SERVER['DOCUMENT_ROOT'] ?? '';
$scriptFilename = $_SERVER['SCRIPT_FILENAME'] ?? '';
$scriptName = $_SERVER['SCRIPT_NAME'] ?? '';
$phpSelf = $_SERVER['PHP_SELF'] ?? '';
$remoteAddr = $_SERVER['REMOTE_ADDR'] ?? '';
$connection = $_SERVER['HTTP_CONNECTION'] ?? '';
$host = $_SERVER['HTTP_HOST'] ?? '';
$referer = $_SERVER['HTTP_REFERER'] ?? '';
$userAgent = $_SERVER['HTTP_USER_AGENT'] ?? '';
$queryString = $_SERVER['QUERY_STRING'] ?? '';
$requestUri = $_SERVER['REQUEST_URI'] ?? '';
?>
```

## Get super global
```php
<?php
 
echo isset($_GET["name"]) ? $_GET["name"] : "";
 
echo $_GET["name"] ?? "";
 
echo htmlspecialchars($_GET["name"] ?? "");
 
?>
```

## Post super global
```php
<?php
// print_r($_POST);
 
$title = '';
$description = '';
 
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['submit'])) {
    global $title;
    global $description;
    $title = htmlspecialchars($_POST['title']);
    $description = htmlspecialchars($_POST['description']);
}
```

## Files super global
```php
<?php
$title = '';
$description = '';
$submitted = false;
$file = null;

if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['submit'])) {
    $title = htmlspecialchars($_POST['title'] ?? '');
    $description = htmlspecialchars($_POST['description'] ?? '');
    $submitted = true;
    $file = $_FILES['logo'];

    if ($file['error'] === UPLOAD_ERR_OK) {
        $uploadDir = 'uploads/';

        if (!is_dir($uploadDir)) {
            mkdir($uploadDir, 0755, true);
        }

        $filename = uniqid() . '-' . $file['name'];
        $allowedExtensions = ['jpg', 'jpeg', 'png'];
        $fileExtension = strtolower(pathinfo($filename, PATHINFO_EXTENSION));

        if (in_array($fileExtension, $allowedExtensions)) {
            if (move_uploaded_file($file['tmp_name'], $uploadDir . $filename)) {
                echo 'File uploaded';
            }
        } else {
            echo 'File not allowed';
        }
    }
}
?>
```

## Session super global
```php
#index.php

<?php
 
session_start();
 
$_SESSION['name'] = 'John';
 
print_r($_SESSION);


#checksession.php
<?php
session_start();
 
if (isset($_SESSION['name']))
    echo $_SESSION['name'];
else echo "Not set";


#destroy.php
<?php
session_start();
 
// unsets name
// unset($_SESSION['name']);
 
// mostly used when using authentication
session_destroy();
```

## Cookie super global
```php
#index.php
<?php
 
setcookie('username', 'jdoe', time() + 3600, '/');

#checkcookie.php
<?php
 
$username =  ($_COOKIE['username']) ?? "Guest";
 
?>
 
<p>Welcome <?= $username ?></p>

#destroycookie.php
<?php
setcookie('username', '', time() - 3600, '/');
```