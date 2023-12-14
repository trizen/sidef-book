[1]: https://rosettacode.org/wiki/Lucas-Carmichael_numbers

# [Lucas-Carmichael numbers][1]

The function is also built-in as **n.lucas\_carmichael(A,B)**.

```ruby
func LC_in_range(A, B, k) {

    var LC = []

    func (m, L, lo, k) {

        var hi = idiv(B,m).iroot(k)

        if (lo > hi) {
            return nil
        }

        if (k == 1) {

            hi = min(B.isqrt, hi)
            lo = max(lo, idiv_ceil(A, m))
            lo > hi && return nil

            var t = mulmod(m.invmod(L), -1, L)

            t > hi && return nil
            t += L while (t < lo)

            for p in (range(t, hi, L).primes) {
                with (m*p) {|n|
                    LC << n if (p+1 `divides` n+1)
                }
            }

            return nil
        }

        each_prime(lo, hi, {|p|
            __FUNC__(m*p, lcm(L, p+1), p+1, k-1) if m.is_coprime(p+1)
        })
    }(1, 1, 3, k)

    return LC.sort
}

func LC_with_n_primes(n) {
    return nil if (n < 3)

    var x = pn_primorial(n+1)/2
    var y = 2*x

    loop {
        var arr = LC_in_range(x,y,n)
        arr && return arr[0]
        x = y+1
        y = 2*x
    }
}

func LC_count(A, B) {
    var count = 0
    for k in (3..Inf) {
        if (pn_primorial(k+1)/2 > B) {
            break
        }
        count += LC_in_range(A,B,k).len
    }
    return count
}

say "Least Lucas-Carmichael number with n prime factors:"

for n in (3..12) {
    say "#{'%2d'%n}: #{LC_with_n_primes(n)}"
}

say "\nNumber of Lucas-Carmichael numbers less than 10^n:"

var acc = 0
for n in (1..10) {
    var c = LC_count(10**(n-1), 10**n)
    say "#{'%2d'%n}: #{c + acc}"
    acc += c
}
```

#### Output:
```
Least Lucas-Carmichael number with n prime factors:
 3: 399
 4: 8855
 5: 588455
 6: 139501439
 7: 3512071871
 8: 199195047359
 9: 14563696180319
10: 989565001538399
11: 20576473996736735
12: 4049149795181043839

Number of Lucas-Carmichael numbers less than 10^n:
 1: 0
 2: 0
 3: 2
 4: 8
 5: 26
 6: 60
 7: 135
 8: 323
 9: 791
10: 1840
```
