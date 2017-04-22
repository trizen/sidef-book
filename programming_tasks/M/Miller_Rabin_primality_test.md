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
        var a = irand(2, n-1)
        var x = expmod(a, d, n)
        next if (x ~~ [1, n-1])

        (s-1).times {
            x = expmod(x, 2, n)
            return false if x==1
            break if (x == n-1)
        }
        return false if (x != n-1)
    }

    return true
}

say {|n| is_prime(n, 10) }.grep(^1000).join(', ')
```
