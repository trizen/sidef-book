[1]: http://rosettacode.org/wiki/Prime_decomposition

# [Prime decomposition][1]

Using the _ntheory_ library (very fast):

```ruby
require('ntheory')
func prime_factors(n) {
    [%S<ntheory>.factor(n.to_s)]
}
```


Trial division:

```python
func prime_factors(n) {
    var p = 3
    var out = []
    return out if (n < 1)
    while (!(n & 1)) {
        n >>= 1
        out << 2
    }
    while ((n > 1) && (p*p <= n)) {
        while (n %% p) {
            n /= p
            out << p
        }
        p += 2
    }
    out << n if (n > 1)
    return out
}
```


Calling the function:

```ruby
say prime_factors(536870911)
```

#### Output:
```
[233, 1103, 2089]
```
