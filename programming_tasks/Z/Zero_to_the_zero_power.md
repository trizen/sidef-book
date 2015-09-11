[1]: http://rosettacode.org/wiki/Zero_to_the_zero_power

# [Zero to the zero power][1]

```ruby
[0, Complex(0, 0)].each {|n|
    say n**n;
    say n.pow(n);
    say pow(n, n);
    say Math.pow(n, n);
}
```

#### Output:
```
1
1
1
1
1
1
1
1
```


However, taking the 0'th root of a number and raising it back to the zero power, we get the following results:

```ruby
say 0.root(0).pow(0);       # => "NaN"
say ((0**(1/0))**0);        # => "inf"
```
