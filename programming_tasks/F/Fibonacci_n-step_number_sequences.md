[1]: http://rosettacode.org/wiki/Fibonacci_n-step_number_sequences

# [Fibonacci n-step number sequences][1]

```ruby
func fib(n, xs=[1], k=20) {
    loop {
        var len = xs.len
        len >= k && break
        xs << xs.ft(max(0, len - n)).sum
    }
    return xs
}

for i in (2..10) {
    say fib(i).join(' ')
}
say fib(2, [2, 1]).join(' ')
```

#### Output:
```
1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597 2584 4181 6765
1 1 2 4 7 13 24 44 81 149 274 504 927 1705 3136 5768 10609 19513 35890 66012
1 1 2 4 8 15 29 56 108 208 401 773 1490 2872 5536 10671 20569 39648 76424 147312
1 1 2 4 8 16 31 61 120 236 464 912 1793 3525 6930 13624 26784 52656 103519 203513
1 1 2 4 8 16 32 63 125 248 492 976 1936 3840 7617 15109 29970 59448 117920 233904
1 1 2 4 8 16 32 64 127 253 504 1004 2000 3984 7936 15808 31489 62725 124946 248888
1 1 2 4 8 16 32 64 128 255 509 1016 2028 4048 8080 16128 32192 64256 128257 256005
1 1 2 4 8 16 32 64 128 256 511 1021 2040 4076 8144 16272 32512 64960 129792 259328
1 1 2 4 8 16 32 64 128 256 512 1023 2045 4088 8172 16336 32656 65280 130496 260864
2 1 3 4 7 11 18 29 47 76 123 199 322 521 843 1364 2207 3571 5778 9349
```

Using matrix exponentiation:

```ruby
func fibonacci_matrix(k) is cached {
    Matrix.build(k,k, {|i,j|
        ((i == k-1) || (i == j-1)) ? 1 : 0
    })
}

func fibonacci_kth_order(n, k=2) {
    var A = fibonacci_matrix(k)
    (A**n)[0][-1]
}

for k in (2..9) {
    say ("Fibonacci of k=#{k} order: ", (15+k).of { fibonacci_kth_order(_, k) })
}
```

#### Output:
```
Fibonacci of k=2 order: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987]
Fibonacci of k=3 order: [0, 0, 1, 1, 2, 4, 7, 13, 24, 44, 81, 149, 274, 504, 927, 1705, 3136, 5768]
Fibonacci of k=4 order: [0, 0, 0, 1, 1, 2, 4, 8, 15, 29, 56, 108, 208, 401, 773, 1490, 2872, 5536, 10671]
Fibonacci of k=5 order: [0, 0, 0, 0, 1, 1, 2, 4, 8, 16, 31, 61, 120, 236, 464, 912, 1793, 3525, 6930, 13624]
Fibonacci of k=6 order: [0, 0, 0, 0, 0, 1, 1, 2, 4, 8, 16, 32, 63, 125, 248, 492, 976, 1936, 3840, 7617, 15109]
Fibonacci of k=7 order: [0, 0, 0, 0, 0, 0, 1, 1, 2, 4, 8, 16, 32, 64, 127, 253, 504, 1004, 2000, 3984, 7936, 15808]
Fibonacci of k=8 order: [0, 0, 0, 0, 0, 0, 0, 1, 1, 2, 4, 8, 16, 32, 64, 128, 255, 509, 1016, 2028, 4048, 8080, 16128]
Fibonacci of k=9 order: [0, 0, 0, 0, 0, 0, 0, 0, 1, 1, 2, 4, 8, 16, 32, 64, 128, 256, 511, 1021, 2040, 4076, 8144, 16272]
```

Faster algorithm:

```ruby
func fibonacci_kth_order (n, k = 2) {

    return 0 if (n < k-1)

    var f = (1..(k+1) -> map {|j|
        j < k ? 2**j : 1
    })

    k += 1

    for i in (2*(k-1) .. n) {
        f[i%k] = (2*f[(i-1)%k] - f[i%k])
    }

    return f[n%k]
}

for k in (2..9) {
    say ("Fibonacci of k=#{k} order: ", (15+k).of { fibonacci_kth_order(_, k) })
}
```

(same output as above)
