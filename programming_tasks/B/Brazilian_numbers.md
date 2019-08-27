[1]: https://rosettacode.org/wiki/Brazilian_numbers

# [Brazilian numbers][1]

```ruby
func is_Brazilian_prime(q) {
 
    static L = Set()
    static M = 0
 
    return true  if L.has(q)
    return false if (q < M)
 
    var N = (q<1000 ? 1000 : 2*q)
 
    for K in (primes(3, ilog2(N+1))) {
        for n in (2 .. iroot(N-1, K-1)) {
            var p = (n**K - 1)/(n-1)
            L << p if (p<N && p.is_prime)
        }
    }
 
    M = (L.max \\ 0)
    return L.has(q)
}
 
func is_Brazilian(n) {
 
    if (!n.is_prime) {
        n.is_square || return (n>6)
        var m = n.isqrt
        return (m>3 && (!m.is_prime || m==11))
    }
 
    is_Brazilian_prime(n)
}
 
 
with (20) {|n|
    say "First #{n} Brazilian numbers:"
    say (^Inf -> lazy.grep(is_Brazilian).first(n))
 
    say "\nFirst #{n} odd Brazilian numbers:"
    say (^Inf -> lazy.grep(is_Brazilian).grep{.is_odd}.first(n))
 
    say "\nFirst #{n} prime Brazilian numbers"
    say (^Inf -> lazy.grep(is_Brazilian).grep{.is_prime}.first(n))
}
```

#### Output:
```
First 20 Brazilian numbers:
[7, 8, 10, 12, 13, 14, 15, 16, 18, 20, 21, 22, 24, 26, 27, 28, 30, 31, 32, 33]

First 20 odd Brazilian numbers:
[7, 13, 15, 21, 27, 31, 33, 35, 39, 43, 45, 51, 55, 57, 63, 65, 69, 73, 75, 77]

First 20 prime Brazilian numbers
[7, 13, 31, 43, 73, 127, 157, 211, 241, 307, 421, 463, 601, 757, 1093, 1123, 1483, 1723, 2551, 2801]
```


Extra:

```ruby
for n in (1..6) {
    say ("#{10**n->commify}th Brazilian number = ", is_Brazilian.nth(10**n))
}
```

#### Output:
```
10th Brazilian number = 20
100th Brazilian number = 132
1,000th Brazilian number = 1191
10,000th Brazilian number = 11364
100,000th Brazilian number = 110468
1,000,000th Brazilian number = 1084566
```
