---
layout: home
title: Class basics
parent: Php
---


## Class basics
```php
<?php

class User
{
  // Properties
  public $name;
  public $email;

  public function __construct($name, $email)
  {
    $this->name = $name;
    $this->email = $email;
  }

  // Methods
  public function login()
  {
    echo $this->name . ' logged in <br>';
  }
}

// Instantiate a new object
$user1 = new User('John Doe', 'john@gmail.com');

$user1->login();

$user2 = new User('Jane Doe', 'jane@gmail.com');

$user2->login();

// var_dump($user2);
```

## Static method and functions
```php
<?php

class MathUtility
{
  public static $pi = 3.14159;

  public static function add(...$nums)
  {
    return array_sum($nums);
  }
}

# :: is scope resolution operator
echo MathUtility::$pi . '<br>';
echo MathUtility::add(1, 2, 3, 4, 5) . '<br>';
```

## Abstract class
```php
<?php
abstract class Shape
{
  protected $name;

  // Abstract method to calculate area
  abstract public function calculateArea();

  // Constructor
  public function __construct($name)
  {
    $this->name = $name;
  }

  // Concrete method
  public function getName()
  {
    return $this->name;
  }
}

class Circle extends Shape
{
  private $radius;

  public function __construct($name, $radius)
  {
    parent::__construct($name);
    $this->radius = $radius;
  }

  // Implement the abstract method to calculate area for a circle
  public function calculateArea()
  {
    return pi() * pow($this->radius, 2);
  }
}

class Rectangle extends Shape
{
  private $width;
  private $height;

  public function __construct($name, $width, $height)
  {
    parent::__construct($name);
    $this->width = $width;
    $this->height = $height;
  }

  // Implement the abstract method to calculate area for a rectangle
  public function calculateArea()
  {
    return $this->width * $this->height;
  }
}

// Create instances of concrete classes
$circle = new Circle('Circle', 5);
$rectangle = new Rectangle('Rectangle', 4, 6);

// Call methods on objects
echo $circle->getName() . ' Area: ' . $circle->calculateArea() . '<br>';
echo $rectangle->getName() . ' Area: ' . $rectangle->calculateArea() . '<br>';
```

## Interface
```php
<?php
interface ContentInterface
{
  public function display();
  public function edit();
}

class Article implements ContentInterface
{
  private $title;
  private $content;

  public function __construct($title, $content)
  {
    $this->title = $title;
    $this->content = $content;
  }

  public function display()
  {
    echo "<h2>{$this->title}</h2>";
    echo "<p>{$this->content}</p>";
  }

  public function edit()
  {
    echo "Editing the article '{$this->title}'";
  }
}

class Video implements ContentInterface
{
  private $title;
  private $url;

  public function __construct($title, $url)
  {
    $this->title = $title;
    $this->url = $url;
  }

  public function display()
  {
    echo "<h2>{$this->title}</h2>";
    echo "<iframe src='{$this->url}'></iframe>";
  }

  public function edit()
  {
    echo "Editing the video '{$this->title}'";
  }
}

$article = new Article('Introduction to PHP', 'PHP is a versatile scripting language...');
$video = new Video('PHP For Beginners', 'https://www.youtube.com/embed/1_gLbLPx2T8');
?>

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.tailwindcss.com"></script>

  <title>PHP From Scratch</title>
</head>

<body class="bg-gray-100">
  <header class="bg-blue-500 text-white p-4">
    <div class="container mx-auto">
      <h1 class="text-3xl font-semibold">PHP From Scratch</h1>
    </div>
  </header>
  <div class="container mx-auto p-4 mt-4">
    <div class="bg-white rounded-lg shadow-md p-6 mt-6">
      <?= $article->display() ?>
    </div>
    <div class="bg-white rounded-lg shadow-md p-6 mt-6">
      <?= $video->display() ?>
    </div>
  </div>
</body>

</html>
```

## The key principles in OOP are:
1. Inheritance
2. Polymorphism
3. Encapsulation
4. Abstraction

### 1. Inheritance:

Inheritance is a mechanism in OOP that allows a new class (subclass/derived class) to inherit properties and behaviors from an existing class (superclass/base class). The subclass can reuse and extend the functionality of the superclass.

**Example:**

```php
class Animal {
    public function eat() {
        echo "Animal is eating.";
    }
}

class Dog extends Animal {
    public function bark() {
        echo "Dog is barking.";
    }
}

$dog = new Dog();
$dog->eat();  // Inherited method from Animal class
$dog->bark(); // Method specific to Dog class
```

In this example, `Dog` inherits the `eat` method from the `Animal` class. It's a way to represent an "is-a" relationship (e.g., a Dog is an Animal).

### 2. Polymorphism:

Polymorphism allows objects of different classes to be treated as objects of a common base class. It enables the same method or operation to behave differently based on the context of its use.

**Example:**

```php
interface Shape {
    public function calculateArea();
}

class Circle implements Shape {
    private $radius;

    public function __construct($radius) {
        $this->radius = $radius;
    }

    public function calculateArea() {
        return pi() * $this->radius * $this->radius;
    }
}

class Square implements Shape {
    private $side;

    public function __construct($side) {
        $this->side = $side;
    }

    public function calculateArea() {
        return $this->side * $this->side;
    }
}

$circle = new Circle(5);
$square = new Square(4);

echo $circle->calculateArea(); // Polymorphism in action
echo $square->calculateArea(); // Polymorphism in action
```

Here, `Circle` and `Square` both implement the `Shape` interface, and they provide their own implementation of the `calculateArea` method. This allows us to treat objects of different shapes uniformly through the common interface.

### 3. Encapsulation:

Encapsulation is the bundling of data (attributes) and the methods that operate on the data into a single unit (class). It hides the internal implementation details and exposes only what is necessary. Access to the data is typically controlled through getter and setter methods.

**Example:**

```php
class Person {
    private $name;
    private $age;

    public function __construct($name, $age) {
        $this->name = $name;
        $this->age = $age;
    }

    public function getName() {
        return $this->name;
    }

    public function getAge() {
        return $this->age;
    }

    public function setAge($age) {
        if ($age >= 0) {
            $this->age = $age;
        }
    }
}

$person = new Person("John", 25);
echo $person->getName(); // Accessing data through getter method
$person->setAge(26);      // Modifying data through setter method
echo $person->getAge();   // Accessing modified data through getter method
```

In this example, the `Person` class encapsulates the attributes (`$name` and `$age`). Access to these attributes is controlled through getter and setter methods. This helps in maintaining the integrity of the object's state and allows controlled access to its internal representation.

### 4. Abstraction:

Abstraction is the process of simplifying complex systems by modeling classes based on the essential properties and behaviors they possess, while ignoring unnecessary details. It involves defining a set of abstract classes or interfaces that represent the common characteristics of a group of related objects.

**Example:**

```php
abstract class Shape {
    abstract public function calculateArea();
}

class Circle extends Shape {
    private $radius;

    public function __construct($radius) {
        $this->radius = $radius;
    }

    public function calculateArea() {
        return pi() * $this->radius * $this->radius;
    }
}

class Square extends Shape {
    private $side;

    public function __construct($side) {
        $this->side = $side;
    }

    public function calculateArea() {
        return $this->side * $this->side;
    }
}
```

In this example, `Shape` is an abstract class that declares an abstract method `calculateArea()`. Concrete classes like `Circle` and `Square` extend this abstract class and provide their specific implementation of the `calculateArea` method. The abstraction allows us to talk about shapes in general, without worrying about the specific details of each shape.