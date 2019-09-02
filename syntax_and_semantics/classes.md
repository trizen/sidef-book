# Classes

A class is a declaration of a constructor of objects with a specific type. Each object has zero or more attributes (instance variables) with zero or more behaviours (methods), that are defined inside a specific class or inherited from super-classes.

```ruby
class Person (name, age, address) {
    method position {
        # GPS.locate(self.address)
    }

    method increment_age(amount=1) {
         self.age += amount
    }
}

var obj = Person(
       name: "Foo",
        age: 50,
    address: "St. Bar"
)

say obj.age                # prints: 50
say obj.name               # prints: "Foo"
say obj.address            # prints: "St. Bar"

obj.name = "Baz"           # changes name to "Baz"
say obj.name               # prints: "Baz"

obj.increment_age          # increments age by 1
say obj.age                # prints: 51
```

### Class attributes

The attributes of a class can be either specified as parameters, or declared with the `has` keyword.

```ruby
class Example(a, b) {
   has c = 3
   has d = a+c
}

var obj = Example(1, 2)

say obj.a   #=> 1
say obj.b   #=> 2
say obj.c   #=> 3
say obj.d   #=> 4
```

### Class initialization

Extra object-initialization setup can be done by defining a method named `init`, which will be called automatically called whenever a new instance-object is created.

```ruby
class Example (a, b) {

   has r = 0

   method init {      # called automatically
      r = a+b
   }

   method foo {
      r
   }
}

var obj = Example(3, 4)
say obj.foo              #=> 7
```

### Class variables

The syntax `ClassName!var_name` can be used for defining, accessing or modifying a class variable.

```ruby
class Example {

    Example!hidden = 'secret'    # global class variable

    method concat (str) {
        str + ' ' + Example!hidden
    }
}

var x = Example()
var y = Example()

say x.concat('foo')   #=> 'foo secret'
say y.concat('bar')   #=> 'bar secret'

Example!hidden = 'public'  # changing the class variable

say x.concat('foo')   #=> 'foo public'
say y.concat('bar')   #=> 'bar public'
```

The modification of a class variable can be localized by prefixing the declaration with the `local` keyword:

```ruby
local Example!hidden = 'local value'
```

### Class inheritance (experimental)

Inheritance of behaviors and attributes, by a given class, is declared with the `<` operator, followed by the name of the class from which the current class inherits:

```ruby
class Animal(String name, Number age)  {
    method speak { "..." }
}

class Dog(String color) < Animal {
    method speak { "woof" }
    method ageHumanYears { self.age * 7 }
}

class Cat < Animal {
    method speak { "meow" }
}

var dog = Dog(name: "Sparky", age: 6, color: "white")
var cat = Cat(name: "Mitten", age: 3)

say dog.speak          #=> woof
say cat.speak          #=> meow
say cat.age            #=> 3
say dog.ageHumanYears  #=> 42
say dog.color          #=> white
```

Multiple inheritance is declared with the `<<` operator, followed by two or more class names, separated by commas:

```ruby
class Camera { }
class MobilePhone { }
class CameraPhone << Camera, MobilePhone { }
```
