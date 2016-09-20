[1]: http://rosettacode.org/wiki/Perfect_numbers

# [Perfect numbers][1]

```ruby
func is_perfect(n) {
    var sum = 0
    for i in (1 ..^ n) {
        i.divides(n) && (sum += i)
    }
    sum == n
}
 
10000.times { |i|
    is_perfect(i) && say i
}
```

For even perfect numbers, we can have a much faster check:

```ruby
func is_even_perfect(n) {

    var square = (8*n + 1)
    square.is_sqr || return false

    var tp = ((square.isqrt + 1) / 2)
    tp.is_pow || return false

    (tp-1).is_prime ? true : false
}

for i in range(0, 10000, 2) {
    is_even_perfect(i) && say i
}
```

#### Output:
```
6
28
496
8128
```
