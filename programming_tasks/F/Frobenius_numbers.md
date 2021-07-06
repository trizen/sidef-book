[1]: https://rosettacode.org/wiki/Frobenius_numbers

# [Frobenius numbers][1]

```ruby
func frobenius_number(n) {
    prime(n) * prime(n+1) - prime(n) - prime(n+1)
}
 
say gather {
    1..Inf -> each {|k|
        var n = frobenius_number(k)
        break if (n >= 10_000)
        take(n)
    }
}
```

#### Output:
```
[1, 7, 23, 59, 119, 191, 287, 395, 615, 839, 1079, 1439, 1679, 1931, 2391, 3015, 3479, 3959, 4619, 5039, 5615, 6395, 7215, 8447, 9599]
```
