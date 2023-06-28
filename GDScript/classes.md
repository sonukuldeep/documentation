---
layout: home
title: Classes
parent: GDScript
---

## Classes

Classes combine data and functions. In the Godot API (Application Programming Interface) there are many pre-defined classes. These classes are documented in the API section of the official documentation.

When we want to use a class we usually create a new instance of it. This new instance of the class is an object with a unique reference. For example, the Nodes of a scene in Godot are instances of classes.

We create a new scene by extending an existing class such as Node2D. That’s why the first line of code says what class is being extended.

The data of a class are stored in variables that we call properties. And the functions are called methods. When we extend a class, we gain access to its properties and methods. Also, we can add our own properties and methods to extend the functionality.

Some methods may be replaced by our own such as the _ready and _process functions. These are called virtual methods and have a name prefixed by an underscore. In most of the code examples so far, we replaced the _ready function in the extended Node2D class.

Once we have saved a scene, we may reuse it in other scenes by creating new instances of it. In fact, we have created a new unnamed class. To give our class a name, we may use the ‘class_name’ keyword to register it as a new type in Godot’s editor.

Example of extending and naming a new class:
```py
class_name Motorcycle extends Node2D

# Add properties
export(String) var make = "Kawasaki"
export(int) var cc = 900
export(Color, RGB) var color = ColorN("Ninja Green")
var fuel = 0.0
var speed = 0.0

# Override virtual methods
func _ready():
	add_fuel(17.3)

func _process(delta):
	if fuel > 0.0:
		speed += delta
		fuel -= delta
		print(speed, "km/h")

# Add a new method
func add_fuel(litres):
	fuel += litres
```

### OOP

Writing programs using Classes is called Object Orientated Programming or OOP for short. It helps us to organize the functionality of a large project into manageable chunks of related functionality (using encapsulation).

The way to arrange the modules (code architecture) has been described as various well-known design patterns. These are used in Godot, and here are some examples:

- Singleton pattern — using an Autoload script to store global data and globally accessible functions
- Observer pattern — using signals to emit to observers (connected scripts)
- Factory pattern — using an Autoload scene to store predefined nodes and have a generator function to provide an instance of one of these nodes

### Inheritance

Godot makes extensive use of Class Inheritance as may be seen in the built-in Node hierarchy. Starting with the most basic Class called Object. This is extended to create the Node class. Then Node is extended to create Node2D, Spatial and Control classes.

In the Editor, we can see the Class hierarchy when we go to add a new node to our scene. Also, the Inspector panel lists the chain of classes that comprise any node that we are inspecting.

### Composition

Another OOP concept is Composition. This is where a class is composed of instances of other classes. We compose a scene in our game by adding Instances of various nodes. Our scene may then be given a class_name value. Although, in most cases we don’t bother.