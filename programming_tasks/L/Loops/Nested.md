[1]: http://rosettacode.org/wiki/Loops/Nested

# [Loops/Nested][1]

```ruby
var arr = 10.of{ 10.of{ 20.irand + 1 } }

for row in arr {
    for num in row {
        "%3d".printf(num);
        num == 20 && goto :OUT
    }
    print "\n"
} @:OUT

print "\n"
```

#### Output:
```
  9 17 14 17 17  7  1  3  9 18
  1 12  1 19  9  5  1 17 19  3
 17  2 18 12 15 10  8 13 13 14
 12 16 13 13  2 11  3 15  2  4
 15 15  8 11  5  2  1 16  8 13
 17  3  1  1  8 12  4 20
```
