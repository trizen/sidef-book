# Types

In Sidef, a new type can be declared as a class and its name can be used in function or method parameters to provide dynamic type checking:

```ruby
class Point(Number x, Number y) {
    method to_s { "Point(#{x}, #{y})" }      # auto-stringification
}

func foo(Point p) {
    say p
}

foo(Point(5, 6))
```

A type can be veryfied by using the `.kind_of(TYPE)` method, which is defined inside the `Object` class, which is the parent of all classes (including user-defined classes):

```ruby
say "foo".kind_of(String)     #=> true
say "bar".kind_of(Number)     #=> false
```

The type of an object can be found usind the following two methods (which are also defined inside the `Object` class):

```ruby
say "foo".ref           #=> Sidef::Types::String::String
say "foo".class         #=> String
```
