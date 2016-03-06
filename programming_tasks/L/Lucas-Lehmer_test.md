[1]: http://rosettacode.org/wiki/Lucas-Lehmer_test

# [Lucas-Lehmer test][1]

```ruby
require('ntheory');
 
func is_prime(n) {
    %S'ntheory'.is_prime(n);
}
 
func is_mersenne_prime(p) {
    p == 2 && return(true);
    var s = 4;
    var mp = (2**p - 1);
    (p-3).times {
      s = (s.expmod(2, mp) - 2);
      s < 0 && (s += mp);
    }
    s == 0;
}
 
Inf.times { |n|
       is_prime(n)
    && is_mersenne_prime(n)
    && say "M#{n}";
}
```

#### Output:
```
M2
M3
M5
M7
M13
M17
M19
M31
M61
M89
M107
M127
M521
M607
M1279
^C
```
