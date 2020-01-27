[1]: http://rosettacode.org/wiki/Bernoulli_numbers

# [Bernoulli numbers][1]

Built-in:

```ruby
say bernoulli(42).as_frac    #=> 1520097643918070802691/1806
```

Recursive solution (with auto-memoization):

```ruby
func bernoulli_number(n) is cached {

    n.is_one && return 1/2
    n.is_odd && return   0

    1 - sum(^n, {|k|
        binomial(n,k) * __FUNC__(k) / (n - k + 1)
    })
}

for n in (0..60) {
    var Bn = bernoulli_number(n) || next
    printf("B(%2d) = %44s / %s\n", n, Bn.nude)
}
```

Using Ramanujan's congruences (pretty fast):

```ruby
func ramanujan_bernoulli_number(n) is cached {

    return 1/2 if n.is_one
    return 0   if n.is_odd

    ((n%6 == 4 ? -1/2 : 1) * (n+3)/3 - sum(1 .. (n - n%6)/6, {|k|
        binomial(n+3, n - 6*k) * __FUNC__(n - 6*k)
    })) / binomial(n+3, n)
}
```

Using Euler's product formula for the Riemann zeta function and the Von Staudt–Clausen theorem (very fast):

```ruby
func bernoulli_number_from_zeta(n) {

    n.is_zero && return   1
    n.is_one  && return 1/2
    n.is_odd  && return   0

    var log2B = (log(4*Num.tau*n)/2 + n*log(n) - n*log(Num.tau) - n)/log(2)
    local Num!PREC = *(int(n + log2B) + (n <= 90 ? 18 : 0))

    var K = 2*(n! / Num.tau**n)
    var d = n.divisors.grep {|k| is_prime(k+1) }.prod {|k| k+1 }
    var z = ceil((K*d).root(n-1)).primes.prod {|p| 1 - p.float**(-n) }

    (-1)**(n/2 + 1) * int(ceil(d*K / z)) / d
}
```

The Akiyama–Tanigawa algorithm:

```ruby
func bernoulli_print {
    var a = []
    for m in (0..60) {
        a << 1/(m+1)
        for j in (1..m -> flip) {
            (a[j-1] -= a[j]) *= j
        }
        a[0] || next
        printf("B(%2d) = %44s / %s\n", m, a[0].nude)
    }
}

bernoulli_print()
```

#### Output:
```
B( 0) =                                            1 / 1
B( 1) =                                            1 / 2
B( 2) =                                            1 / 6
B( 4) =                                           -1 / 30
B( 6) =                                            1 / 42
B( 8) =                                           -1 / 30
B(10) =                                            5 / 66
B(12) =                                         -691 / 2730
B(14) =                                            7 / 6
B(16) =                                        -3617 / 510
B(18) =                                        43867 / 798
B(20) =                                      -174611 / 330
B(22) =                                       854513 / 138
B(24) =                                   -236364091 / 2730
B(26) =                                      8553103 / 6
B(28) =                                 -23749461029 / 870
B(30) =                                8615841276005 / 14322
B(32) =                               -7709321041217 / 510
B(34) =                                2577687858367 / 6
B(36) =                        -26315271553053477373 / 1919190
B(38) =                             2929993913841559 / 6
B(40) =                       -261082718496449122051 / 13530
B(42) =                       1520097643918070802691 / 1806
B(44) =                     -27833269579301024235023 / 690
B(46) =                     596451111593912163277961 / 282
B(48) =                -5609403368997817686249127547 / 46410
B(50) =                  495057205241079648212477525 / 66
B(52) =              -801165718135489957347924991853 / 1590
B(54) =             29149963634884862421418123812691 / 798
B(56) =          -2479392929313226753685415739663229 / 870
B(58) =          84483613348880041862046775994036021 / 354
B(60) = -1215233140483755572040304994079820246041491 / 56786730
```
