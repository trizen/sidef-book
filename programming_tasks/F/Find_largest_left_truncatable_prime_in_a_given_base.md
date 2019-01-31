[1]: http://rosettacode.org/wiki/Find_largest_left_truncatable_prime_in_a_given_base

# [Find largest left truncatable prime in a given base][1]

```ruby
func lltp(n) {
    var b = 1
    var best = nil
    var v = (n-1 -> primes)

    while (v) {
        best = v.max
        b *= n
        v.map! { |vi|
            {|i| i*b + vi }.map(1..^n).grep{.is_prime}...
        }
    }

    return best
}

for i in (3..17) {
    printf("%2d %s\n", i, lltp(i))
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

Alternative solution:

```ruby
func digits2num(digits, base) {
    digits.map_kv {|k,v| base**k * v  }.sum
}

func generate_from_suffix(p, base) {

    var seq = [p]

    for n in (1 ..^ base) {
        var t = [p..., n]
        if (is_prime(digits2num(t, base))) {
            seq << __FUNC__(t, base)...
        }
    }

    return seq
}

func left_truncatable_primes(base) {

    var prime_digits = (base-1 -> primes)

    prime_digits.map  {|p| generate_from_suffix([p], base)... }\
                .map  {|t| digits2num(t, base) }\
                .sort
}

for n in (3..11) {
    var ltp = left_truncatable_primes(n)
    say ("There are #{'%4d' % ltp.len} left-truncatable primes in base #{'%2d' % n}, where largest is #{ltp.max}")
}
```

#### Output:
```
There are    3 left-truncatable primes in base  3, where largest is 23
There are   16 left-truncatable primes in base  4, where largest is 4091
There are   15 left-truncatable primes in base  5, where largest is 7817
There are  454 left-truncatable primes in base  6, where largest is 4836525320399
There are   22 left-truncatable primes in base  7, where largest is 817337
There are  446 left-truncatable primes in base  8, where largest is 14005650767869
There are  108 left-truncatable primes in base  9, where largest is 1676456897
There are 4260 left-truncatable primes in base 10, where largest is 357686312646216567629137
There are   75 left-truncatable primes in base 11, where largest is 2276005673
```
