[1]: http://rosettacode.org/wiki/Perfect_numbers

# [Perfect numbers][1]

```ruby
func is_perfect(n) {
    var sum = 0;
    range(1, n-1).each { |i|
        i.divides(n) && (sum += i);
    };
    sum == n;
}
 
range(1, 1000).each { |i|
    is_perfect(i) && say i;
}
```

#### Output:
```
6
28
496
```