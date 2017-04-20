[1]: http://rosettacode.org/wiki/100_doors

# [100 doors][1]

*Unoptimized*

```ruby
var doors = []

for pass (1..100) {
    for i (1..100) {
        if (i % pass == 0) {
            doors[i] := false -> not!
        }
    }
}

for i (1..100) {
    "Door %3d is %s\n".printf(i, doors[i] ? 'open' : 'closed')
}
```


*Optimized*

```ruby
for i (1..100) {
    "Door %3d is %s\n".printf(i, ["closed", "open"][i -> is_sqr])
}
```
