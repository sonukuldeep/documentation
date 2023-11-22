---
layout: home
title: Looping through array
parent: Php
---


## Looping through array
```php
<ul class="mb-6">
        <?php foreach ($names as $name) : ?>
          <li><?= $name ?></li>
        <?php endforeach; ?>
      </ul>
      <h3 class="text-xl font-semibold mb-4">Using a foreach loop with index</h3>
      <ul class="mb-6">
        <?php foreach ($names as $index => $name) : ?>
          <li><?= $index . ' - ' . $name ?></li>
        <?php endforeach; ?>
      </ul>
      <h3 class="text-xl font-semibold mb-4">Using a foreach loop with associative array</h3>
      <ul class="mb-6">
        <?php foreach ($users as $user) : ?>
          <li><?= $user['name'] . ' - ' . $user['email'] ?></li>
        <?php endforeach; ?>
      </ul>
      <h3 class="text-xl font-semibold mb-4">Getting key names and values from associative array</h3>
      <ul class="mb-6">
        <?php foreach ($users as $user) : ?>
          <?php foreach ($user as $key => $value) : ?>
            <li><?= $key . ' - ' . $value ?></li>
          <?php endforeach; ?>
        <?php endforeach; ?>
      </ul>
```