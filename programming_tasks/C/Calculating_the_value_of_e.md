[1]: https://rosettacode.org/wiki/Calculating_the_value_of_e

# [Calculating the value of e][1]

```ruby
func calculate_e(prec=50) {
    sum(^prec, {|n| 1/n! })
}
 
say calculate_e()
say calculate_e(100).as_dec(100)
```

#### Output:
```
2.7182818284590452353602874713526624977572470937
2.718281828459045235360287471352662497757247093699959574966967627724076630353547594571382178525166427
```