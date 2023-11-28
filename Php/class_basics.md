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