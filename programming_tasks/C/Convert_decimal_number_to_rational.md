[1]: https://rosettacode.org/wiki/Convert_decimal_number_to_rational

# [Convert decimal number to rational][1]

By default, literal numbers are represented in rational form:

```ruby
say 0.75.as_frac          #=> 3/4
say 0.518518.as_frac      #=> 259259/500000
say 0.9054054.as_frac     #=> 4527027/5000000
```

Additionally, `Num(str)` can be used for parsing a decimal expansion into rational form:

```ruby
'0.9054054 0.518518 0.75'.split.each { |str|
    say Num(str).as_frac
}
```

#### Output:
```
4527027/5000000
259259/500000
3/4
```

For rational approximations, the Number `.rat_approx` method can be used:

```ruby
say 0.518518.rat_approx.as_frac    #=> 14/27
say 0.9054054.rat_approx.as_frac   #=> 67/74
```
