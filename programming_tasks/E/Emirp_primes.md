[1]: https://rosettacode.org/wiki/Emirp_primes

# [Emirp primes][1]

```ruby
func forprimes(a, b, callback) {
    for (var p = a.dec.next_prime; p <= b; p.next_prime!) {
        callback(p)
    }
}
 
func is_emirp(p) {
    var str = Str(p)
    var rev = str.reverse
    (str != rev) && is_prime(Num(rev))
}
 
func emirp_list(count) {
    var i = 13
    var inc = (100 + 10*count)
    var n = []
    while (n.len < count) {
        forprimes(i, i+inc - 1, {|p|
            is_emirp(p) && (n << p)
        })
        (i, inc) = (i+inc, int(inc * 1.03) + 1000)
    }
    n.splice(count)
    return n
}
 
say ("First 20: ", emirp_list(20).join(' '))
say ("Between 7700 and 8000: ", gather {
        forprimes(7700, 8000, {|p| is_emirp(p) && take(p) })
    }.join(' '))
say ("The 10,000'th emirp: ", emirp_list(10000)[-1])
```

#### Output:
```
First 20: 13 17 31 37 71 73 79 97 107 113 149 157 167 179 199 311 337 347 359 389
Between 7700 and 8000: 7717 7757 7817 7841 7867 7879 7901 7927 7949 7951 7963
The 10,000'th emirp: 948349
```