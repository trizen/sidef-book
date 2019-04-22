[1]: http://rosettacode.org/wiki/Perfect_numbers

# [Perfect numbers][1]

```ruby
func is_perfect(n) {
    n.sigma == 2*n
}

for n in (1..10000) {
    say n if is_perfect(n)
}
```

Alternatively, a more efficient check for even perfect numbers:

```ruby
func is_even_perfect(n) {

    var square = (8*n + 1)
    square.is_square || return false

    var t = ((square.isqrt + 1) / 2)
    t.is_smooth(2) || return false

    t-1 -> is_prime
}

for n in (1..10000) {
    say n if is_even_perfect(n)
}
```

#### Output:
```
6
28
496
8128
```
