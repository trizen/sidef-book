[1]: https://rosettacode.org/wiki/Odd_and_square_numbers

# [Odd and square numbers][1]

```ruby
var lo = 100
var hi = 1_000
 
say gather {
    for k in (lo.isqrt .. hi.isqrt) {
        take(k**2) if k.is_odd
    }
}
```

#### Output:
```
[121, 169, 225, 289, 361, 441, 529, 625, 729, 841, 961]
```
