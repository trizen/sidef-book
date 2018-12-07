[1]: https://rosettacode.org/wiki/Sexy_primes

# [Sexy primes][1]

```ruby
func tuple_tail (n, cnt, array) {
 
    n = array.len if (n > array.len)
 
    var tail = []
    for k in (1..n) {
        var p = array[-n + k - 1]
        tail << ("(" + { 6*_ + p }.map(^cnt).join(' ') + ")")
    }
    return tail
}
 
func sexy_string(p) {
    is_prime(p+6) || is_prime(p-6) ? 'sexy' : 'unsexy'
}
 
var max = 1_000_035
var primes = Hash()
 
for (var p = 2; p < max; p.next_prime!) {
    primes{sexy_string(p)} := [] << p
    p+ 6 < max && is_prime(p+ 6) ? (primes{'pair'}       := [] << p) : next
    p+12 < max && is_prime(p+12) ? (primes{'triplet'}    := [] << p) : next
    p+18 < max && is_prime(p+18) ? (primes{'quadruplet'} := [] << p) : next
    p+24 < max && is_prime(p+24) ? (primes{'quintuplet'} := [] << p) : next
}
 
say "Total primes less than #{max}: #{primes{:sexy}.len + primes{:unsexy}.len}\n"
 
for sexy,cnt in ([['pair', 2], ['triplet', 3], ['quadruplet', 4], ['quintuplet', 5]]) {
    say "Number of sexy prime #{sexy}s less than #{max}: #{primes{sexy}.len}"
    say "   Last 5 sexy prime #{sexy}s less than #{max}: #{tuple_tail(5, cnt, primes{sexy}).join(' ')}\n"
}
 
say "Number of unsexy primes less than #{max}: #{primes{:unsexy}.len}"
say "  Last 10 unsexy primes less than #{max}: #{primes{:unsexy}.last(10)}"
```

#### Output:
```
Total primes less than 1000035: 78500

Number of sexy prime pairs less than 1000035: 16386
   Last 5 sexy prime pairs less than 1000035: (999371 999377) (999431 999437) (999721 999727) (999763 999769) (999953 999959)

Number of sexy prime triplets less than 1000035: 2900
   Last 5 sexy prime triplets less than 1000035: (997427 997433 997439) (997541 997547 997553) (998071 998077 998083) (998617 998623 998629) (998737 998743 998749)

Number of sexy prime quadruplets less than 1000035: 325
   Last 5 sexy prime quadruplets less than 1000035: (977351 977357 977363 977369) (983771 983777 983783 983789) (986131 986137 986143 986149) (990371 990377 990383 990389) (997091 997097 997103 997109)

Number of sexy prime quintuplets less than 1000035: 1
   Last 5 sexy prime quintuplets less than 1000035: (5 11 17 23 29)

Number of unsexy primes less than 1000035: 48627
  Last 10 unsexy primes less than 1000035: [999853, 999863, 999883, 999907, 999917, 999931, 999961, 999979, 999983, 1000003]
```