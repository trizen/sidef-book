[1]: https://rosettacode.org/wiki/Euclid-Mullin_sequence

# [Euclid-Mullin sequence][1]

```ruby
func f(n) is cached {
    return 2 if (n == 1)
    lpf(1 + prod(1..^n, {|k| f(k) }))
}
 
say f.map(1..16)
say f.map(17..27)
```

#### Output:
```
[2, 3, 7, 43, 13, 53, 5, 6221671, 38709183810571, 139, 2801, 11, 17, 5471, 52662739, 23003]
[30693651606209, 37, 1741, 1313797957, 887, 71, 7127, 109, 23, 97, 159227]
```
