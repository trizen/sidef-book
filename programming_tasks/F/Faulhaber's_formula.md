[1]: http://rosettacode.org/wiki/Faulhaber's_formula

# [Faulhaber's formula][1]

```ruby
func faulhaber_s_formula(p) {

    var formula = gather {
        for j in ^(p+1) {
            take "(#{binomial(p+1, j) * j.bernfrac -> as_rat})*n^#{p+1 - j}"
        }
    }

    formula.grep! { !.contains('(0)*') }.join!(' + ')

    formula -= /\(1\)\*/g
    formula -= /\^1\b/g
    formula.gsub!(/\(([^+]*?)\)/, {|a| a })

    "1/#{p + 1} * (#{formula})"
}

for p in ^10 {
    printf("%2d: %s\n", p, faulhaber_s_formula(p))
}
```

#### Output:
```
 0: 1/1 * (n)
 1: 1/2 * (n^2 + n)
 2: 1/3 * (n^3 + 3/2*n^2 + 1/2*n)
 3: 1/4 * (n^4 + 2*n^3 + n^2)
 4: 1/5 * (n^5 + 5/2*n^4 + 5/3*n^3 + -1/6*n)
 5: 1/6 * (n^6 + 3*n^5 + 5/2*n^4 + -1/2*n^2)
 6: 1/7 * (n^7 + 7/2*n^6 + 7/2*n^5 + -7/6*n^3 + 1/6*n)
 7: 1/8 * (n^8 + 4*n^7 + 14/3*n^6 + -7/3*n^4 + 2/3*n^2)
 8: 1/9 * (n^9 + 9/2*n^8 + 6*n^7 + -21/5*n^5 + 2*n^3 + -3/10*n)
 9: 1/10 * (n^10 + 5*n^9 + 15/2*n^8 + -7*n^6 + 5*n^4 + -3/2*n^2)
```

By not simplifying the formulas, we have a much clearer code:

```ruby
func faulhaber_s_formula(p) {

    var formula = gather {
        for j in ^(p+1) {
            take "#{binomial(p+1, j) * j.bernfrac -> as_rat}*n^#{p+1 - j}"
        }
    }.join(' + ')

    "1/#{p + 1} * (#{formula})"
}

for p in ^10 {
    printf("%2d: %s\n", p, faulhaber_s_formula(p))
}
```
