[1]: https://rosettacode.org/wiki/Jordan-Pólya_numbers

# [Jordan-Pólya numbers][1]

```ruby
func jordan_pólya_numbers(n, k, F, callback) {

    var factors = F.sort.uniq
    var factors_end = factors.end

    if (k == 0) {
        callback(1)
        return nil
    }

    func (m, k, i=0) {

        if (k == 1) {

            var L = idiv(n,m)

            for j in (i..factors_end) {
                with (factors[j]) {|q|
                    q > L && break
                    callback(m*q)
                }
            }

            return nil
        }

        var L = idiv(n,m).iroot(k)

        for j in (i..factors_end) {
            with (factors[j]) { |q|
                q > L && break
                __FUNC__(m*q, k-1, j)
            }
        }
    }(1, k)

    return nil
}

func inverse_factorial_W(n) {
    var l = (log(n) - log(Num.tau)/2)
    l / lambert_w(l / Num.e) - 1/2
}

var limit = 100e6
var factors = (2..inverse_factorial_W(limit).int -> map { .factorial })
var terms = Set()

for k in (0 .. limit.ilog2) {
    jordan_pólya_numbers(limit, k, factors, {|v| terms << v })
}

terms.sort!

say "The first 50 Jordan-Pólya numbers:"
terms.first(50).each_slice(10, {|*a|
    a.map { '%5s' % _ }.join(' ').say
})

say "\nThere are #{terms.len} Jordan-Pólya numbers <= #{limit.commify}, where largest is #{terms.last}."
```

#### Output:
```
The first 50 Jordan-Pólya numbers:
    1     2     4     6     8    12    16    24    32    36
   48    64    72    96   120   128   144   192   216   240
  256   288   384   432   480   512   576   720   768   864
  960  1024  1152  1296  1440  1536  1728  1920  2048  2304
 2592  2880  3072  3456  3840  4096  4320  4608  5040  5184

There are 367 Jordan-Pólya numbers <= 100,000,000, where largest is 99532800.
```
