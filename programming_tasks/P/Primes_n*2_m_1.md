[1]: https://rosettacode.org/wiki/Primes:_n*2^m%2B1

# [Primes: n*2^m+1][1]

Takes ~2 seconds to run.

```ruby
for n in (1..400) {
    var p = (^Inf -> lazy.map {|m| [m, n * 2**m + 1] }.first_by { .tail.is_prime })
    printf("%3s %4s: %s\n", n, p...)
}
```


(same output as the Perl version)
