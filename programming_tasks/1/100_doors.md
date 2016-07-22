[1]: http://rosettacode.org/wiki/100_doors

# [100 doors][1]

*Unoptimized*

```ruby
var doors = [];
 
100.times { |pass|
    100.times { |i|
        if (i % pass == 0) {
            doors[i] := false -> not!
        }
    }
}
 
100.times { |i|
    "Door %3d is %s\n".printf(i, doors[i] ? 'open' : 'closed')
}
```


*Optimized*

```ruby
{ |i|
    "Door %3d is %s\n".printf(i, ["closed", "open"][i.is_sqr])
} * 100
```
