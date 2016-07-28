[1]: http://rosettacode.org/wiki/Perfect_numbers

# [Perfect numbers][1]

```ruby
func is_perfect(n) {
    var sum = 0;
    for i in (1 ..^ n) {
        i.divides(n) && (sum += i);
    }
    sum == n;
}
 
1000.times { |i|
    is_perfect(i) && say i;
}
```

#### Output:
```
6
28
496
```
