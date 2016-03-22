# Subsets

A subset is a definition which specifies the upper limit of inheritance, with optional argument validation.

```ruby
subset Integer     < Number  { |n| n.is_int }
subset Natural     < Integer { |n| n.is_pos }
subset EvenNatural < Natural { |n| n.is_even }

func foo(n < EvenNatural) {
     say n
}

foo(42)         # ok
foo(43)         # failed assertion at run-time
```

In some sense, a subset is the opposite of a type. For example, let's consider the following class hierarchy:

```ruby
class Hello(name) {
    method greet { say "Hello, #{self.name}!" }
}

class Hi < Hello {
    method greet { say "Hi, #{self.name}!" }
}

class Hey < Hi {
    method greet { say "Hey, #{self.name}!" }
}
```

If we declare a function that accepts a subset of `Hi`, it can also accept `Hello`, but it cannot accept `Hey`:

```ruby
func greet(obj < Hi) { obj.greet }       # `Hi` is the upper limit

greet(Hi("Foo"))        # ok
greet(Hello("Bar"))     # ok
greet(Hey("Baz"))       # fail: `Hey` is too evolved
```

On the other hand, if we use `Hi` as a type assertion, it will accept `Hey`, but not `Hello`:

```ruby
func greet(Hi > obj) { obj.greet }       # `Hi` is the lower limit

greet(Hi("Foo"))        # ok
greet(Hey("Baz"))       # ok
greet(Hello("Bar"))     # fail: `Hello` is too primitive
```
