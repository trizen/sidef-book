[1]: https://rosettacode.org/wiki/Sexy_primes

# [Sexy primes][1]

```ruby
var limit  = 1e6+35
var primes = limit.primes

say "Total number of primes <= #{limit.commify} is #{primes.len.commify}."
say "Sexy k-tuple primes <= #{limit.commify}:\n"

(2..5).each {|k|
    var groups = []
    primes.each {|p|
        var group = (1..^k -> map {|j| 6*j + p })
        if (group.all{.is_prime} && (group[-1] <= limit)) {
            groups << [p, group...]
        }
    }

    say "...total number of sexy #{k}-tuple primes = #{groups.len.commify}"
    say "...where last 5 tuples are: #{groups.last(5).map{'('+.join(' ')+')'}.join(' ')}\n"
}

var unsexy_primes = primes.grep {|p| is_prime(p+6) || is_prime(p-6) -> not }
say "...total number of unsexy primes = #{unsexy_primes.len.commify}"
say "...where last 10 unsexy primes are: #{unsexy_primes.last(10)}"
```

#### Output:
```
Total number of primes <= 1,000,035 is 78,500.
Sexy k-tuple primes <= 1,000,035:

...total number of sexy 2-tuple primes = 16,386
...where last 5 tuples are: (999371 999377) (999431 999437) (999721 999727) (999763 999769) (999953 999959)

...total number of sexy 3-tuple primes = 2,900
...where last 5 tuples are: (997427 997433 997439) (997541 997547 997553) (998071 998077 998083) (998617 998623 998629) (998737 998743 998749)

...total number of sexy 4-tuple primes = 325
...where last 5 tuples are: (977351 977357 977363 977369) (983771 983777 983783 983789) (986131 986137 986143 986149) (990371 990377 990383 990389) (997091 997097 997103 997109)

...total number of sexy 5-tuple primes = 1
...where last 5 tuples are: (5 11 17 23 29)

...total number of unsexy primes = 48,627
...where last 10 unsexy primes are: [999853, 999863, 999883, 999907, 999917, 999931, 999961, 999979, 999983, 1000003]
```
