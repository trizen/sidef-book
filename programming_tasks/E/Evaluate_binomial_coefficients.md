[1]: https://rosettacode.org/wiki/Evaluate_binomial_coefficients

# [Evaluate binomial coefficients][1]

Straightforward translation of the formula:

```ruby
func binomial(n,k) {
    n! / ((n-k)! * k!)
}
 
say binomial(400, 200)
```

Alternatively, by using the `Number.binomial()` function:

```ruby
say binomial(400,200)
```
