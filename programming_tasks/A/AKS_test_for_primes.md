[1]: https://rosettacode.org/wiki/AKS_test_for_primes

# [AKS test for primes][1]

```ruby
func binprime(p) {
    p >= 2 || return false
    for i in (1 .. p>>1) {
        (binomial(p, i) % p) && return false
    }
    return true
}

func coef(n, e) {
    (e == 0) && return "#{n}"
    (n == 1) && (n = "")
    (e == 1) ? "#{n}x" : "#{n}x^#{e}"
}

func binpoly(p) {
    join(" ", coef(1, p), ^p -> map {|i|
        join(" ", %w(+ -)[(p-i)&1], coef(binomial(p, i), i))
    }.reverse...)
}

say "expansions of (x-1)^p:"
for i in ^10 { say binpoly(i) }
say "Primes to 80: [#{2..80 -> grep { binprime(_) }.join(' ')}]"
```

#### Output:
```
expansions of (x-1)^p:
1
x - 1
x^2 - 2x + 1
x^3 - 3x^2 + 3x - 1
x^4 - 4x^3 + 6x^2 - 4x + 1
x^5 - 5x^4 + 10x^3 - 10x^2 + 5x - 1
x^6 - 6x^5 + 15x^4 - 20x^3 + 15x^2 - 6x + 1
x^7 - 7x^6 + 21x^5 - 35x^4 + 35x^3 - 21x^2 + 7x - 1
x^8 - 8x^7 + 28x^6 - 56x^5 + 70x^4 - 56x^3 + 28x^2 - 8x + 1
x^9 - 9x^8 + 36x^7 - 84x^6 + 126x^5 - 126x^4 + 84x^3 - 36x^2 + 9x - 1
Primes to 80: [2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79]
```
