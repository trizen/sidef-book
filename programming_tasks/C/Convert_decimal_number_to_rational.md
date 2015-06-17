[1]: http://rosettacode.org/wiki/Convert_decimal_number_to_rational

# [Convert decimal number to rational][1]

This can be done by using the "to_r" method, which converts a scalar-object into a rational number:

```ruby
'0.9054054 0.518518 0.75'.split.each { |d|
    say d.to_r;
}
```


Another way is by using the "r" suffix on number literals:

```ruby
say 0.9054054r;
say 0.518518r;
say 0.75r;
```

#### Output:
```
4527027/5000000
259259/500000
3/4
```