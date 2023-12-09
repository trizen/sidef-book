[1]: https://rosettacode.org/wiki/Factors_of_an_integer

# [Factors of an integer][1]

Built-in:

```ruby
say divisors(97)    #=> [1, 97]
say divisors(2695)  #=> [1, 5, 7, 11, 35, 49, 55, 77, 245, 385, 539, 2695]
```

Trial-division (slow for large n):

```ruby
func divisors(n) {
  gather {
    { |d|
        take(d, n//d) if d.divides(n)
    } << 1..n.isqrt
  }.sort.uniq
}

[53, 64, 32766].each {|n|
    say "divisors(#{n}): #{divisors(n)}"
}
```

#### Output:
```
divisors(53): [1, 53]
divisors(64): [1, 2, 4, 8, 16, 32, 64]
divisors(32766): [1, 2, 3, 6, 43, 86, 127, 129, 254, 258, 381, 762, 5461, 10922, 16383, 32766]
```
