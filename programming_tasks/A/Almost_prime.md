[1]: https://rosettacode.org/wiki/Almost_prime

# [Almost prime][1]

```ruby
func is_k_almost_prime(n, k) {
    for (var (p, f) = (2, 0); (f < k) && (p*p <= n); ++p) {
        (n /= p; ++f) while (p `divides` n)
    }
    n > 1 ? (f+1 == k) : (f == k)
}

{ |k|
    var x = 10
    say gather {
        { |i|
            if (is_k_almost_prime(i, k)) {
                take(i)
                --x == 0 && break
            }
        } << 1..Inf
    }
} << 1..5
```

#### Output:
```
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
[4, 6, 9, 10, 14, 15, 21, 22, 25, 26]
[8, 12, 18, 20, 27, 28, 30, 42, 44, 45]
[16, 24, 36, 40, 54, 56, 60, 81, 84, 88]
[32, 48, 72, 80, 108, 112, 120, 162, 168, 176]
```
