[1]: https://rosettacode.org/wiki/Verify_distribution_uniformity/Chi-squared_test

# [Verify distribution uniformity/Chi-squared test][1]

```ruby
# Confluent hypergeometric function of the first kind F_1(a;b;z)
func F1(a, b, z, limit=100) {
    sum(0..limit, {|k|
        rising_factorial(a, k) / rising_factorial(b, k) * z**k / k!
    })
}
 
func γ(a,x) {    # lower incomplete gamma function γ(a,x)
    #a**(-1) * x**a * F1(a, a+1, -x)            # simpler formula
    a**(-1) * x**a * exp(-x) * F1(1, a+1, x)    # slightly better convergence
}
 
func P(a,z) {    # regularized gamma function P(a,z)
    γ(a,z) / Γ(a)
}
 
func chi_squared_cdf (k, x) {
    var f = (k<20 ? 20 : 10)
    given(x) {
        when (0) { 0 }
        case (. < (k + f*sqrt(k))) { P(k/2, x/2) }
        else { 1 }
    }
}
 
func chi_squared_test(arr, significance = 0.05) {
    var n = arr.len
    var N = arr.sum
    var expected = N/n
    var χ_squared = arr.sum_by {|v| (v-expected)**2 / expected }
    var p_value = (1 - chi_squared_cdf(n-1, χ_squared))
    [χ_squared, p_value, p_value > significance]
}
 
[
    %n< 199809 200665 199607 200270 199649 >,
    %n< 522573 244456 139979  71531  21461 >,
].each {|dataset|
    var r = chi_squared_test(dataset)
    say "data: #{dataset}"
    say "χ² = #{r[0]}, p-value = #{r[1].round(-4)}, uniform = #{r[2]}\n"
}
```

#### Output:
```
data: [199809, 200665, 199607, 200270, 199649]
χ² = 4.14628, p-value = 0.3866, uniform = true

data: [522573, 244456, 139979, 71531, 21461]
χ² = 790063.27594, p-value = 0, uniform = false
```
