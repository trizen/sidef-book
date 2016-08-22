# Lazy evaluation

Lazy evaluation is a common feature in functional programming languages and provides an way to delay the evaluation of an expression until the result is actually needed.

By default, Sidef is an eagerly evaluated language, but it supports a form of lazy evaluation, provided by the method `Object.lazy()`, almost in the same way as Ruby does:

```ruby
say (^Inf -> lazy.grep{ .is_prime }.first(10))     # first 10 primes
```

The `.lazy` method returns a Lazy object, which behaves almost like an Array, except that it executes the methods in a pipeline fashion and dynamically stops when no more elements are required, without creating any temporary arrays in memory:

```ruby
for line in (DATA.lazy.grep{ _ < 'd' }.map{ print ">> "; .uc }) {
   print line
}

__DATA__
a
b
c
d
```

Output (which shows that `.map{}` is really lazy):

```text
>> A
>> B
>> C
```

This mechanism is generic enough to support any kind of object that implements the `.iter()` method, which returns a Block that gives back one element at a time when it's called with no arguments. When the iteration ends, it must return `nil`.

```ruby
class Example(data) {
    method iter {
        var p = 0
        {
            data[p++]
        }
    }
}

var obj = Example([1,2,3,4,5])
say obj.lazy.grep{.is_prime}.to_a       # filters all the primes lazily
```

Currently, the `.iter()` method is defined in the following built-in types: Array, String, FileHandle, DirHandle, RangeString, RangeNumber and Lazy.
