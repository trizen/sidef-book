[1]: http://rosettacode.org/wiki/Time_a_function

# [Time a function][1]

```ruby
var benchmark = frequire('Benchmark')

func fac_rec(n) {
    n == 0 ? 1 : (n * __FUNC__(n - 1))
}

func fac_iter(n) {
    var prod = 1
    n.times { |i|
        prod *= i
    }
    prod
}

var result = benchmark.timethese(-3, Hash(
    'fac_rec'  => { fac_rec(20)  },
    'fac_iter' => { fac_iter(20) },
))

benchmark.cmpthese(result)
```

#### Output:
```
Benchmark: running fac_iter, fac_rec for at least 3 CPU seconds...
  fac_iter:  3 wallclock secs ( 3.23 usr +  0.00 sys =  3.23 CPU) @ 7331.89/s (n=23682)
   fac_rec:  3 wallclock secs ( 3.19 usr +  0.00 sys =  3.19 CPU) @ 3551.72/s (n=11330)
           Rate  fac_rec fac_iter
fac_rec  3552/s       --     -52%
fac_iter 7332/s     106%       --
```
