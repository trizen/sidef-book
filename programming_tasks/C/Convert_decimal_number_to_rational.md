[1]: http://rosettacode.org/wiki/Convert_decimal_number_to_rational

# [Convert decimal number to rational][1]

This can be done by using the _num_ method, which converts a scalar-object into a number, followed by the _as_rat_ method, which converts it back into a string as a fraction:

```ruby
'0.9054054 0.518518 0.75'.words.each { |d|
    say Num(d).as_rat
}
```


Another way is by calling the _as_rat_ method directly on Number objects:

```ruby
say 0.9054054.as_rat
say 0.518518.as_rat
say 0.75.as_rat
```

#### Output:
```
4527027/5000000
259259/500000
3/4
```
