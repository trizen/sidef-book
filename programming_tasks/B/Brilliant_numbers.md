[1]: https://rosettacode.org/wiki/Brilliant_numbers

# [Brilliant numbers][1]

```ruby
func is_briliant_number(n) {
    n.is_semiprime && (n.factor.map{.len}.uniq.len == 1)
}
 
func brilliant_numbers_count(n) {
 
    var count = 0
    var len = n.isqrt.len
 
    for k in (1 .. len-1) {
        var pi = prime_count(10**(k-1), 10**k - 1)
        count += binomial(pi, 2)+pi
    }
 
    var min = (10**(len - 1))
    var max = (10**len - 1)
 
    each_prime(min, max, {|p|
        count += prime_count(p, max `min` idiv(n, p))
    })
 
    return count
}
 
say "First 100 brilliant numbers:"
 
100.by(is_briliant_number).each_slice(10, {|*a|
    say a.map { '%4s' % _}.join(' ')
})
 
say ''
 
for n in (1 .. 12) {
    var v = (10**n .. Inf -> first_by(is_briliant_number))
    printf("First brilliant number >= 10^%d is %s", n, v)
    printf(" at position %s\n", brilliant_numbers_count(v))
}
```

#### Output:
```
First 100 brilliant numbers:
   4    6    9   10   14   15   21   25   35   49
 121  143  169  187  209  221  247  253  289  299
 319  323  341  361  377  391  403  407  437  451
 473  481  493  517  527  529  533  551  559  583
 589  611  629  649  667  671  689  697  703  713
 731  737  767  779  781  793  799  803  817  841
 851  869  871  893  899  901  913  923  943  949
 961  979  989 1003 1007 1027 1037 1067 1073 1079
1081 1121 1139 1147 1157 1159 1189 1207 1219 1241
1247 1261 1271 1273 1333 1343 1349 1357 1363 1369

First brilliant number >= 10^1 is 10 at position 4
First brilliant number >= 10^2 is 121 at position 11
First brilliant number >= 10^3 is 1003 at position 74
First brilliant number >= 10^4 is 10201 at position 242
First brilliant number >= 10^5 is 100013 at position 2505
First brilliant number >= 10^6 is 1018081 at position 10538
First brilliant number >= 10^7 is 10000043 at position 124364
First brilliant number >= 10^8 is 100140049 at position 573929
First brilliant number >= 10^9 is 1000000081 at position 7407841
First brilliant number >= 10^10 is 10000600009 at position 35547995
First brilliant number >= 10^11 is 100000000147 at position 491316167
First brilliant number >= 10^12 is 1000006000009 at position 2409600866
```
