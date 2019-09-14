[1]: https://rosettacode.org/wiki/Prime_decomposition

# [Prime decomposition][1]

Built-in:

```ruby
say factor(536870911)      #=> [233, 1103, 2089]
say factor_exp(536870911)  #=> [[233, 1], [1103, 1], [2089, 1]]
```


Trial division:

```python
func prime_factors(n) {
    return [] if (n < 1)
    gather {
        while (!(n & 1)) {
            n >>= 1
            take(2)
        }
        var p = 3
        while ((n > 1) && (p*p <= n)) {
            while (n %% p) {
                n //= p
                take(p)
            }
            p += 2
        }
        take(n) if (n > 1)
    }
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
