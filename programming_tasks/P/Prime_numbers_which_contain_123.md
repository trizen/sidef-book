[1]: https://rosettacode.org/wiki/Prime_numbers_which_contain_123

# [Prime numbers which contain 123][1]

```ruby
func numbers_with_subdigits(upto, base = 10, s = 123.digits(base)) {
    Enumerator({|callback|
        for k in (0 .. base**(upto.len(base) - s.len)) {
 
            var d = k.digits(base)
 
            for i in (0 .. d.len) {
                var n = d.clone.insert(i, s...).digits2num(base)
                callback(n) if (n <= upto)
            }
 
            var z = d.clone.insert(d.len, s...)
            loop {
                var n = z.insert(d.len, 0).digits2num(base)
                (n <= upto) ? callback(n) : break
            }
        }
    })
}
 
say "Decimal primes under 100,000 which contain '123':"
numbers_with_subdigits(1e5).grep { .is_prime }.sort.each_slice(10, {|*a|
    say a.map { '%6s' % _ }.join(' ')
})
 
say ''
 
for n in (4..8) {
    var count = numbers_with_subdigits(10**n).grep { .is_prime }.len
    say "Found #{'%6s' % count.commify} such primes < 10^#{n}"
}
```

#### Output:
```
Decimal primes under 100,000 which contain '123':
  1123   1231   1237   8123  11239  12301  12323  12329  12343  12347
 12373  12377  12379  12391  17123  20123  22123  28123  29123  31123
 31231  31237  34123  37123  40123  41231  41233  44123  47123  49123
 50123  51239  56123  59123  61231  64123  65123  70123  71233  71237
 76123  81233  81239  89123  91237  98123

Found      4 such primes < 10^4
Found     46 such primes < 10^5
Found    451 such primes < 10^6
Found  4,412 such primes < 10^7
Found 43,548 such primes < 10^8
```
