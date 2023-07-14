[1]: https://rosettacode.org/wiki/Modular_exponentiation

# [Modular exponentiation][1]

Built-in:

```ruby
say expmod(
    2988348162058574136915891421498819466320163312926952423791023078876139,
    2351399303373464486466122544523690094744975233415544072992656881240319,
    10**40)
```


User-defined:

```ruby
func expmod(a, b, n) {
    var c = 1
    do {
        (c *= a) %= n if b.is_odd
        (a *= a) %= n
    } while (b //= 2)
    c
}
```

#### Output:
```
1527229998585248450016808958343740453059
```
