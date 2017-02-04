[1]: http://rosettacode.org/wiki/Miller–Rabin_primality_test

# [Miller–Rabin primality test][1]

```ruby
func is_prime(n, k) {

    n == 2 && return true
    n <= 1 && return false
    n  & 1 || return false

    var d = n-1
    var s = valuation(d, 2)
    d >>= s

    k.times {
        var a = 2.irand(n)
        var x = expmod(a, d, n)
        next if (x ~~ [1, n-1])

        (s-1).times {
            x.expmod!(2, n)
            return false if x==1
            break if (x == n-1)
        }
        return false if (x != n-1)
    }

    return true
}

say(^1000->grep {|n| is_prime(n, 10) }.join(', '))
```
