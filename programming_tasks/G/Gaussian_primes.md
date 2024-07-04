[1]: https://rosettacode.org/wiki/Gaussian_primes

# [Gaussian primes][1]

```ruby
func gaussianprimes(size) {
    var plot = (2*size + 1 -> of { 2*size + 1 -> of(' ') })
    var primes = []
    for A in (-size .. size) {
        var limit = isqrt(size**2 - A**2)
        for B in (-limit .. limit) {
            var n = Gauss(A, B)
            if (n.is_prime) {
                primes << n.to_n
                plot[B + size + 1][A + size + 1] = 'X'
            }
        }
    }
    return (plot, primes)
}

with(10) {|n|
    var(_plot, primes) = gaussianprimes(n)
    say "Primes within #{n}:"
    primes.slices(10).each { .map{'%7s'%_}.join(", ").say }
}

with (50) {|n|
    var (plot) = gaussianprimes(n)
    say "\nPlot within #{n}"
    plot.each { .join('').say }
}
```

#### Output:
```
Primes within 10:
-9 - 4i, -9 + 4i, -8 - 5i, -8 - 3i, -8 + 3i, -8 + 5i, -7 - 2i,      -7, -7 + 2i, -6 - 5i
-6 - 1i, -6 + 1i, -6 + 5i, -5 - 8i, -5 - 6i, -5 - 4i, -5 - 2i, -5 + 2i, -5 + 4i, -5 + 6i
-5 + 8i, -4 - 9i, -4 - 5i, -4 - 1i, -4 + 1i, -4 + 5i, -4 + 9i, -3 - 8i, -3 - 2i,      -3
-3 + 2i, -3 + 8i, -2 - 7i, -2 - 5i, -2 - 3i, -2 - 1i, -2 + 1i, -2 + 3i, -2 + 5i, -2 + 7i
-1 - 6i, -1 - 4i, -1 - 2i, -1 - 1i, -1 + 1i, -1 + 2i, -1 + 4i, -1 + 6i,     -7i,     -3i
     3i,      7i,  1 - 6i,  1 - 4i,  1 - 2i,  1 - 1i,  1 + 1i,  1 + 2i,  1 + 4i,  1 + 6i
 2 - 7i,  2 - 5i,  2 - 3i,  2 - 1i,  2 + 1i,  2 + 3i,  2 + 5i,  2 + 7i,  3 - 8i,  3 - 2i
      3,  3 + 2i,  3 + 8i,  4 - 9i,  4 - 5i,  4 - 1i,  4 + 1i,  4 + 5i,  4 + 9i,  5 - 8i
 5 - 6i,  5 - 4i,  5 - 2i,  5 + 2i,  5 + 4i,  5 + 6i,  5 + 8i,  6 - 5i,  6 - 1i,  6 + 1i
 6 + 5i,  7 - 2i,       7,  7 + 2i,  8 - 5i,  8 - 3i,  8 + 3i,  8 + 5i,  9 - 4i,  9 + 4i
```


The plot up to 50 is identical to the one produced by the Perl entry.
