# Classes

A class is a declaration of a constructor of objects with a specific type. Each object has zero or more attributes (instance variables) with zero or more behaviours (methods), that are defined inside a specific class or inherited from super-classes.

Inheritance of behaviors and attributes, by a given class, is declared with the `<` operator, followed by the name of the class from which the current class inherits:

```ruby
class Animal(name) {
    method speak {
        say "..."
    }
}

class Dog < Animal {
    method speak {
        say "Woof"
    }
}

class Cat < Animal {
    method speak {
        say "Meow"
    }
}

var dog = Dog("Spot")
var cat = Cat("Garfield")
var animal = Animal("Animal")

dog.speak
cat.speak
animal.speak
```

Output:

```text
Woof
Meow
...
```

Multiple inheritance is declared with the `<<` operator, followed by two or more class names, separated by commas:

```ruby
class Camera { }
class MobilePhone { }
class CameraPhone << Camera, MobilePhone { }
```

Instance variables are public and can be accessed by anyone who has a reference to the object itself:

```ruby
class Person (name, age, address) {
    method walk {
        say "#{name} is walking..."
    }
}

var obj = Person(
    name: "John Smith",
    age: 42,
    address: "St. Bar"
)

say obj.age                #=> 42
say obj.name               #=> "John Smith"
say obj.address            #=> "St. Bar"
```
