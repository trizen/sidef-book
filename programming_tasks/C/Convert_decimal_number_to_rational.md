[1]: http://rosettacode.org/wiki/Convert_decimal_number_to_rational

# [Convert decimal number to rational][1]

This can be done by using the _to_r_ method, which converts a scalar-object into a rational number:

```ruby
'0.9054054 0.518518 0.75'.split.each { |d|
    say d.to_r;
}
```


Another way is by calling the _rat_ method on Number objects:

```ruby
say 0.9054054.rat;
say 0.518518.rat;
say 0.75.rat;
```

#### Output:
```
4527027/5000000
259259/500000
3/4
```