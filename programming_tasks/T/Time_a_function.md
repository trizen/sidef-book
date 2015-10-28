[1]: http://rosettacode.org/wiki/Time_a_function

# [Time a function][1]

```ruby
var benchmark = frequire('Benchmark');
 
func fac_rec(n) {
    n == 0 ? 1 : (n * __FUNC__(n - 1))
}
 
func fac_iter(n) {
    var prod = 1;
    { |i|
        prod *= i;
    } * n;
    prod;
}
 
var result = benchmark.timethese(-3, :(
    'fac_rec'  => func { fac_rec(20)  },
    'fac_iter' => func { fac_iter(20) },
));
 
benchmark.cmpthese(result);
```

#### Output:
```
Benchmark: running fac_iter, fac_rec for at least 3 CPU seconds...
  fac_iter:  3 wallclock secs ( 3.15 usr +  0.00 sys =  3.15 CPU) @ 1745.40/s (n=5498)
   fac_rec:  3 wallclock secs ( 3.21 usr +  0.00 sys =  3.21 CPU) @ 797.51/s (n=2560)
           Rate  fac_rec fac_iter
fac_rec   798/s       --     -54%
fac_iter 1745/s     119%       --
```