[1]: http://rosettacode.org/wiki/Time_a_function

# [Time a function][1]

```ruby
var benchmark = frequire('Benchmark');
 
func fac(n) {
    n == 0 ? 1 : (n * __FUNC__(n - 1))
}
 
func fac_mem(n) {
    static memo = [];
    memo[n] := (n == 0 ? 1 : (n * __FUNC__(n - 1)));
}
 
var result = benchmark.timethese(-3, :(
    'fac'     => func {    fac(10)},
    'fac mem' => func {fac_mem(10)},
));
 
benchmark.cmpthese(result);
```

#### Output:
```
Benchmark: running fac, fac mem for at least 3 CPU seconds...
       fac:  4 wallclock secs ( 3.14 usr +  0.00 sys =  3.14 CPU) @ 127.39/s (n=400)
   fac mem:  3 wallclock secs ( 3.14 usr +  0.00 sys =  3.14 CPU) @ 2407.32/s (n=7559)
          Rate     fac fac mem
fac      127/s      --    -95%
fac mem 2407/s   1790%      --
```