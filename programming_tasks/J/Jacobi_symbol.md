[1]: https://rosettacode.org/wiki/Jacobi_symbol

# [Jacobi symbol][1]

Also built-in as **kronecker(n,k)**.

```ruby
func jacobi(a, n) {

    assert(n > 0,    "#{n} must be positive")
    assert(n.is_odd, "#{n} must be odd")

    var t = 1
    while (a %= n) {
        if (a.is_even) {
            var v = a.valuation(2)
            t *= (-1)**v if (n%8 ~~ [3,5])
            a >>= v
        }
        (a,n) = (n,a)
        t = -t if ([a%4, n%4] == [3,3])
    }

    n==1 ? t : 0
}

for a in (0..50), n in (0..50) {
    assert_eq(jacobi(a, 2*n + 1), kronecker(a, 2*n + 1))
}
```
