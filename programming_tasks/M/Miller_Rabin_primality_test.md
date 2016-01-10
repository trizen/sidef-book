[1]: http://rosettacode.org/wiki/Miller–Rabin_primality_test

# [Miller–Rabin primality test][1]

```ruby
func is_prime(n { .is_odd && (_ > 2) }, k) {
    var s = 0
    var d = n.dec
    (d //= 2; ++s) while d.is_even
 
    k.times {
        var a = 2.irand(n)
        var x = expmod(a, d, n)
        next if (x ~~ [1, n-1])
 
        (s-1).times {
            x.expmod!(2, n)
            return false if x.is_one
            break if (x == n-1)
        }
        return false if (x != n-1)
    }
 
    return true
}
 
func is_prime((2), _k) { true }
func is_prime(_n, _k)  { false }
 
say 1000.range.grep {|n| is_prime(n, 10) }.join(", ")
```