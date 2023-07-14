[1]: https://rosettacode.org/wiki/Factorial

# [Factorial][1]


Recursive:

```ruby
func factorial_recursive(n) {
    n == 0 ? 1 : (n * __FUNC__(n-1))
}
```

Catamorphism:

```ruby
func factorial_reduce(n) {
    1..n -> reduce({|a,b| a * b }, 1)
}
```

Iterative:

```ruby
func factorial_iterative(n) {
    var f = 1
    {|i| f *= i } << 2..n
    return f
}
```

Built-in:

```ruby
say 5!
```
