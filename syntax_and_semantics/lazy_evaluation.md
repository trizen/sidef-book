# Lazy evaluation

Lazy evaluation is a very common feature in functional programming languages and provides an way to delay the evaluation of an expression until the result is actually needed.

By default, Sidef is an eagerly evaluated language, but it still supports a form of lazy evaluation, which is provided by the method `Object.lazy()`:

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

This mechanism is generic enough to support any kind of object that implements the `.iter()` method. Currently, it includes the following built-in types: Array, FileHandle, DirHandle, RangeNumber and Lazy.
