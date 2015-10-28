[1]: http://rosettacode.org/wiki/Percolation/Mean_run_density

# [Percolation/Mean run density][1]

```ruby
func R(n,p) {
    n.of { 1.rand < p ? 1 : 0}.sum;
}
 
const t = 100;
say ('t=', t);
 
range(.1, .9, .2).each { |p|
    printf("p= %f, K(p)= %f\n", p, p*(1-p));
    [10, 100, 1000].each { |n|
        printf (" R(n, p)= %f\n", t.of { R(n, p) }.sum/n / t);
    }
}
```

#### Output:
```
t=100
p= 0.100000, K(p)= 0.090000
 R(n, p)= 0.099000
 R(n, p)= 0.105000
 R(n, p)= 0.099810
p= 0.300000, K(p)= 0.210000
 R(n, p)= 0.301000
 R(n, p)= 0.289800
 R(n, p)= 0.300720
p= 0.500000, K(p)= 0.250000
 R(n, p)= 0.481000
 R(n, p)= 0.501800
 R(n, p)= 0.498260
p= 0.700000, K(p)= 0.210000
 R(n, p)= 0.695000
 R(n, p)= 0.698400
 R(n, p)= 0.701220
p= 0.900000, K(p)= 0.090000
 R(n, p)= 0.910000
 R(n, p)= 0.898500
 R(n, p)= 0.899080
```