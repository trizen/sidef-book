[1]: https://rosettacode.org/wiki/Meissel–Mertens_constant

# [Meissel–Mertens constant][1]

```ruby
var sum = 0
1e7.each_prime {|p|
    with (1f/p) {|t|
        sum += (log(1 - t) + t)
    }
}
say sum+Num.EulerGamma
```

#### Output:
```
0.26149721577767111119422410228297206467931376306
```
