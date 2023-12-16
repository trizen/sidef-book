[1]: https://rosettacode.org/wiki/Golden_ratio/Convergence

# [Golden ratio/Convergence][1]

```ruby
const phi = (1+sqrt(5))/2
func GR(n) is cached { (n == 1) ? 1 : (1 + 1/__FUNC__(n-1)) }

var n = (1..Inf -> first {|n|
    abs(GR(n) - GR(n+1)) <= 1e-5
})

say "#{n} iterations: #{GR(n+1)} (cfrac)\n#{' '*15}#{phi} (actual)"
say "The error is: #{GR(n+1) - phi}"
```

#### Output:
```
14 iterations: 1.6180327868852459016393442622950819672131147541 (cfrac)
               1.61803398874989484820458683436563811772030917981 (actual)
The error is: -0.00000120186464894656524257207055615050719442570740221
```
