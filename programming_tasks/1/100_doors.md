[1]: https://rosettacode.org/wiki/100_doors

# [100 doors][1]

*Unoptimized*

```ruby
var doors = []

{ |pass|
    { |i|
        if (pass `divides` i) {
            doors[i] := false -> not!
        }
    } << 1..100
} << 1..100

{ |i|
    say ("Door %3d is %s" % (i, doors[i] ? 'open' : 'closed'))
} << 1..100
```


*Optimized*

```ruby
{ |i|
    "Door %3d is %s\n".printf(i, <closed open>[i.is_sqr])
} << 1..100
```
