[1]: https://rosettacode.org/wiki/Zero_to_the_zero_power

# [Zero to the zero power][1]

```ruby
[0, Complex(0, 0)].each {|n|
    say n**n
}
```

#### Output:
```
1
1
```


Taking the 0'th root of a number and raising it back to the zero power, we also get a 1:

```ruby
say 0.root(0).pow(0)       # => 1
say ((0**(1/0))**0)        # => 1
```
