[1]: https://rosettacode.org/wiki/Möbius_function

# [Möbius function][1]

Built-in:

```ruby
say moebius(53)    #=> -1
say moebius(54)    #=> 0
say moebius(55)    #=> 1
```


Simple implementation:

```ruby
func μ(n) {
    var f = n.factor_exp.map { .tail }
    f.any { _ > 1 } ? 0 : ((-1)**f.sum)
}
 
with (199) { |n|
    say "Values of the Möbius function for numbers in the range 1..#{n}:"
    [' '] + (1..n->map(μ)) -> each_slice(20, {|*line|
        say line.map { '%2s' % _ }.join(' ')
    })
}
```

#### Output:
```
Values of the Möbius function for numbers in the range 1..199:
    1 -1 -1  0 -1  1 -1  0  0  1 -1  0 -1  1  1  0 -1  0 -1
 0  1  1 -1  0  0  1  0  0 -1 -1 -1  0  1  1  1  0 -1  1  1
 0 -1 -1 -1  0  0  1 -1  0  0  0  1  0 -1  0  1  0  1  1 -1
 0 -1  1  0  0  1 -1 -1  0  1 -1 -1  0 -1  1  0  0  1 -1 -1
 0  0  1 -1  0  1  1  1  0 -1  0  1  0  1  1  1  0 -1  0  0
 0 -1 -1 -1  0 -1  1 -1  0 -1 -1  1  0 -1 -1  1  0  0  1  1
 0  0  1  1  0  0  0 -1  0  1 -1 -1  0  1  1  0  0 -1 -1 -1
 0  1  1  1  0  1  1  0  0 -1  0 -1  0  0 -1  1  0 -1  1  1
 0  1  0 -1  0 -1  1 -1  0  0 -1  0  0 -1 -1  0  0  1  1 -1
 0 -1 -1  1  0  1 -1  1  0  0 -1 -1  0 -1  1 -1  0 -1  0 -1
```
