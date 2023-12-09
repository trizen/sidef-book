[1]: https://rosettacode.org/wiki/Pisano_period

# [Pisano period][1]

```ruby
func pisano_period_pp(p,k) is cached {
 
    assert(k.is_pos,   "k = #{k} must be positive")
    assert(p.is_prime, "p = #{p} must be prime")
 
    var (a, b, n) = (0, 1, p**k)
 
    1..Inf -> first_by {
        (a, b) = (b, (a+b) % n)
        (a == 0) && (b == 1)
    }
}
 
func pisano_period(n) {
    n.factor_map {|p,k| pisano_period_pp(p, k) }.lcm
}
 
say "Pisano periods for squares of primes p <= 15:"
say  15.primes.map {|p| pisano_period_pp(p, 2) }
 
say "\nPisano periods for primes p <= 180:"
say 180.primes.map {|p| pisano_period_pp(p, 1) }

say "\nPisano periods for integers n from 1 to 180:"
say pisano_period.map(1..180)
```

#### Output:
```
Pisano periods for squares of primes p <= 15:
[6, 24, 100, 112, 110, 364]

Pisano periods for primes p <= 180:
[3, 8, 20, 16, 10, 28, 36, 18, 48, 14, 30, 76, 40, 88, 32, 108, 58, 60, 136, 70, 148, 78, 168, 44, 196, 50, 208, 72, 108, 76, 256, 130, 276, 46, 148, 50, 316, 328, 336, 348, 178]

Pisano periods for integers n from 1 to 180:
[1, 3, 8, 6, 20, 24, 16, 12, 24, 60, 10, 24, 28, 48, 40, 24, 36, 24, 18, 60, 16, 30, 48, 24, 100, 84, 72, 48, 14, 120, 30, 48, 40, 36, 80, 24, 76, 18, 56, 60, 40, 48, 88, 30, 120, 48, 32, 24, 112, 300, 72, 84, 108, 72, 20, 48, 72, 42, 58, 120, 60, 30, 48, 96, 140, 120, 136, 36, 48, 240, 70, 24, 148, 228, 200, 18, 80, 168, 78, 120, 216, 120, 168, 48, 180, 264, 56, 60, 44, 120, 112, 48, 120, 96, 180, 48, 196, 336, 120, 300, 50, 72, 208, 84, 80, 108, 72, 72, 108, 60, 152, 48, 76, 72, 240, 42, 168, 174, 144, 120, 110, 60, 40, 30, 500, 48, 256, 192, 88, 420, 130, 120, 144, 408, 360, 36, 276, 48, 46, 240, 32, 210, 140, 24, 140, 444, 112, 228, 148, 600, 50, 36, 72, 240, 60, 168, 316, 78, 216, 240, 48, 216, 328, 120, 40, 168, 336, 48, 364, 180, 72, 264, 348, 168, 400, 120, 232, 132, 178, 120]
```


By assuming that **Wall-Sun-Sun primes** do not exist, we can compute the Pisano period more efficiently, as illustrated below on Fermat numbers **F\_n = 2^(2^n) + 1**:

```ruby
func pisano_period_pp(p, k=1) {
    (p - kronecker(5, p)).divisors.first_by {|d| fibmod(d, p) == 0 } * p**(k-1)
}
 
func pisano_period(n) {
 
    return 0 if (n <= 0)
    return 1 if (n == 1)
 
    var d = n.factor_map {|p,k| pisano_period_pp(p, k) }.lcm
 
    3.times {|k|
        var t = d<<k
        if ((fibmod(t, n) == 0) && (fibmod(t+1, n) == 1)) {
            return t
        }
    }
}
 
for k in (1..8) {
    say ("Pisano(F_#{k}) = ", pisano_period(2**(2**k) + 1))
}
```

#### Output:
```
Pisano(F_1) = 20
Pisano(F_2) = 36
Pisano(F_3) = 516
Pisano(F_4) = 14564
Pisano(F_5) = 2144133760
Pisano(F_6) = 4611702838532647040
Pisano(F_7) = 28356863910078205764000346543980814080
Pisano(F_8) = 3859736307910542962840356678888855900560939475751238269689837480239178278912
```
