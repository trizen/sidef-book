[1]: https://rosettacode.org/wiki/Legendre_prime_counting_function

# [Legendre prime counting function][1]

```ruby
func legendre_phi(x, a) is cached {
    return x if (a <= 0)
    __FUNC__(x, a-1) - __FUNC__(idiv(x, a.prime), a-1)
}
 
func legendre_prime_count(n) is cached {
    return 0 if (n < 2)
    var a = __FUNC__(n.isqrt)
    legendre_phi(n, a) + a - 1
}
 
print("e             n   Legendre    builtin\n",
      "-             -   --------    -------\n")
 
for n in (1 .. 9) {
    printf("%d  %12d %10d %10d\n", n, 10**n,
        legendre_prime_count(10**n), prime_count(10**n))
    assert_eq(legendre_prime_count(10**n), prime_count(10**n))
}
```

#### Output:
```
e             n   Legendre    builtin
-             -   --------    -------
1            10          4          4
2           100         25         25
3          1000        168        168
4         10000       1229       1229
5        100000       9592       9592
6       1000000      78498      78498
7      10000000     664579     664579
```


Alternative implementation of the Legendre phi function, by counting k-rough numbers &lt;= n.

```ruby
func rough_count (n,k) {
 
    # Count of k-rough numbers <= n.
 
    func (n,p) is cached {
 
        if (p > n.isqrt) {
            return 1
        }
 
        if (p == 2) {
            return (n >> 1)
        }
 
        if (p == 3) {
            var t = idiv(n,3)
            return (t - (t >> 1))
        }
 
        var u = 0
        var t = idiv(n,p)
 
        for (var q = 2; q < p; q.next_prime!) {
 
            var v = __FUNC__(t - (t % q), q)
 
            if (v == 1) {
                u += prime_count(q, p-1)
                break
            }
 
            u += v
        }
 
        t - u
    }(n*k, k)
}
 
func legendre_phi(n, a) {
     rough_count(n, prime(a+1))
}
 
func legendre_prime_count(n) is cached {
    return 0 if (n < 2)
    var a = __FUNC__(n.isqrt)
    legendre_phi(n, a) + a - 1
}
 
print("e             n   Legendre    builtin\n",
      "-             -   --------    -------\n")
 
for n in (1 .. 9) {
    printf("%d  %12d %10d %10d\n", n, 10**n,
        legendre_prime_count(10**n), prime_count(10**n))
    assert_eq(legendre_prime_count(10**n), prime_count(10**n))
}
```
