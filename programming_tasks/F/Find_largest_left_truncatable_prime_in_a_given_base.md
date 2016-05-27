[1]: http://rosettacode.org/wiki/Find_largest_left_truncatable_prime_in_a_given_base

# [Find largest left truncatable prime in a given base][1]

```ruby
func primes(n) {
    var (i, j) = (0, 0)
    gather {
        loop {
            i = j.next_prime
            i <= n || break
            take(i)
            j = i
        }
    }
}
 
func lltp(n) {
    var b = 1
    var best = nil
    var v = primes(n-1)
 
    while (v) {
        best = v.max
        b *= n
        v = gather {
            v.each { |vi|
                take((n-1).of { |i| i*b + vi }.grep{.is_prime}...)
            }
        }
    }
 
    return best
}
 
for i in (3..17) {
    printf("%2d %s\n", i, lltp(i))
}
```

#### Output:
```
 3 23
 4 4091
 5 7817
 6 4836525320399
 7 817337
 8 14005650767869
 9 1676456897
10 357686312646216567629137
11 2276005673
12 13092430647736190817303130065827539
13 812751503
14 615419590422100474355767356763
15 34068645705927662447286191
16 1088303707153521644968345559987
17 13563641583101
```