[1]: https://rosettacode.org/wiki/Square_form_factorization

# [Square form factorization][1]

```ruby
const multipliers = divisors(3*5*7*11).grep { _ > 1 }

func sff(N) {

    N.is_prime  && return 1         # n is prime
    N.is_square && return N.isqrt   # n is square

    multipliers.each {|k|

        var P0 = isqrt(k*N)       # P[0]=floor(sqrt(N)
        var Q0 = 1                # Q[0]=1
        var Q  = (k*N - P0*P0)    # Q[1]=N-P[0]^2 & Q[i]
        var P1 = P0               # P[i-1] = P[0]
        var Q1 = Q0               # Q[i-1] = Q[0]
        var P  = 0                # P[i]
        var Qn = 0                # P[i+1]
        var b  = 0                # b[i]

        while (!Q.is_square) {              # until Q[i] is a perfect square
            b = idiv(isqrt(k*N) + P1, Q)    # floor(floor(sqrt(N+P[i-1])/Q[i])
            P = (b*Q - P1)                  # P[i]=b*Q[i]-P[i-1]
            Qn = (Q1 + b*(P1 - P))          # Q[i+1]=Q[i-1]+b(P[i-1]-P[i])
            (Q1, Q, P1) = (Q, Qn, P)
        }

        b  = idiv(isqrt(k*N) + P, Q)        # b=floor((floor(sqrt(N)+P[i])/Q[0])
        P1 = (b*Q0 - P)                     # P[i-1]=b*Q[0]-P[i]
        Q  = (k*N - P1*P1)/Q0               # Q[1]=(N-P[0]^2)/Q[0] & Q[i]
        Q1 = Q0                             # Q[i-1] = Q[0]

        loop {
            b  = idiv(isqrt(k*N) + P1, Q)   # b=floor(floor(sqrt(N)+P[i-1])/Q[i])
            P  = (b*Q - P1)                 # P[i]=b*Q[i]-P[i-1]
            Qn = (Q1 + b*(P1 - P))          # Q[i+1]=Q[i-1]+b(P[i-1]-P[i])
            break if (P == P1)              # until P[i+1]=P[i]
            (Q1, Q, P1) = (Q, Qn, P)
        }
        with (gcd(N,P)) {|g|
            return g if g.is_ntf(N)
        }
    }

   return 0
}

[  11111, 2501, 12851, 13289, 75301, 120787, 967009, 997417,  4558849,  7091569, 13290059,
   42854447, 223553581, 2027651281, 11111111111, 100895598169, 1002742628021, 60012462237239,
   287129523414791, 11111111111111111, 384307168202281507, 1000000000000000127, 9007199254740931,
   922337203685477563, 314159265358979323, 1152921505680588799, 658812288346769681,
   419244183493398773, 1537228672809128917
].each {|n|
    var v = sff(n)
    if    (v == 0) { say "The number #{n} is not factored." }
    elsif (v == 1) { say "The number #{n} is a prime."      }
    else           { say "#{n} = #{[n/v, v].sort.join(' * ')}" }
}
```

#### Output:
```
11111 = 41 * 271
2501 = 41 * 61
12851 = 71 * 181
13289 = 97 * 137
75301 = 257 * 293
120787 = 43 * 2809
967009 = 601 * 1609
997417 = 257 * 3881
4558849 = 383 * 11903
7091569 = 2663 * 2663
13290059 = 3119 * 4261
42854447 = 4423 * 9689
223553581 = 11213 * 19937
2027651281 = 44021 * 46061
11111111111 = 21649 * 513239
100895598169 = 112303 * 898423
The number 1002742628021 is a prime.
60012462237239 = 6862753 * 8744663
287129523414791 = 6059887 * 47381993
^C
```
