[1]: http://rosettacode.org/wiki/100_doors

# [100 doors][1]

*Unoptimized*

```ruby
var doors = [];
 
{ |pass|
    { |i|
        i % pass == 0 && (
            doors[i] := false -> not!
        );
    } * 100;
} * 100;
 
{ |i|
    "Door %3d is %s\n".printf(i, doors[i] ? 'open' : 'closed');
} * 100;
```


*Optimized*

```ruby
{ |i|
    "Door %3d is %s\n".printf(i, ["closed", "open"][i.sqrt.is_int]);
} * 100;
```
