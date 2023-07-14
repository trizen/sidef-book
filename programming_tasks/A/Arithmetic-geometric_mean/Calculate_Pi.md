[1]: https://rosettacode.org/wiki/Arithmetic-geometric_mean/Calculate_Pi

# [Arithmetic-geometric mean/Calculate Pi][1]

```ruby
func agm_pi(digits) {
    var acc = (digits + 8);

    local Num!PREC = 4*digits;

    var an = 1;
    var bn = sqrt(0.5);
    var tn = 0.5**2;
    var pn = 1;

    while (pn < acc) {
        var prev_an = an;
        an = (bn+an / 2);
        bn = sqrt(bn * prev_an);
        prev_an -= an;
        tn -= (pn * prev_an**2);
        pn *= 2;
    }

    ((an+bn)**2 / 4*tn).to_s
}

say agm_pi(100);
```

#### Output:
```
3.141592653589793238462643383279502884197169399375105820974944592307816406286208998628034825342117068
```
