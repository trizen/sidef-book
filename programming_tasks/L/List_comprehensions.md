[1]: http://rosettacode.org/wiki/List_comprehensions

# [List comprehensions][1]

```ruby
var n = 20;
say gather {
    1...n -> each { |x|
         x...n -> each { |y|
           y...n -> each { |z|
             take([x,y,z]) if (x*x + y*y == z*z)
           }
        }
    }
}
```

#### Output:
```
[[3, 4, 5], [5, 12, 13], [6, 8, 10], [8, 15, 17], [9, 12, 15], [12, 16, 20]]
```