[1]: https://rosettacode.org/wiki/Euclidean_rhythm

# [Euclidean rhythm][1]

```ruby
func e(k, n) {
    var s = (^n -> map { |i| i < k ? [1] : [0] })

    var d = (n - k)
    n = max(k, d)
    k = min(k, d)
    var z = d

    while ((z > 0) || (k > 1)) {
        k.times { |i|
            s[i] += s[-1 - i]
        }
        s = s.first(-k)
        z -= k
        d = (n - k)
        n = max(k, d)
        k = min(k, d)
    }

    s.flat.join
}

say e(5, 13)
```

#### Output:
```
1001010010100
```
