[1]: http://rosettacode.org/wiki/Carmichael_3_strong_pseudoprimes

# [Carmichael 3 strong pseudoprimes][1]

```ruby
var ntheory = frequire('ntheory');
 
ntheory.forprimes({ |*p|
   p = Number.new(p[-1]);
   range(2, p-1).each { |h3|
      var ph3 = (p + h3);
      range(1, ph3-1).each { |d|
         ((-p * p) % h3) != (d % h3) && next;
         ((p-1)*ph3) % d && next;
         var q = 1+((p-1) * ph3 / d);
         ntheory.is_prime(q) || next;
         var r = 1+((p*q - 1)/h3);
         ntheory.is_prime(r) || next;
         (q*r) % (p-1) == 1 || next;
         printf("%2d x %5d x %5d = %s\n",p,q,r,ntheory.vecprod(p,q,r));
      }
   }
}, 3, 61);
```

#### Output:
```
 3 x    11 x    17 = 561
 5 x    29 x    73 = 10585
 5 x    17 x    29 = 2465
 5 x    13 x    17 = 1105
 ... full output is 69 lines ...
61 x   661 x  2521 = 101649241
61 x   271 x   571 = 9439201
61 x   241 x   421 = 6189121
61 x  3361 x  4021 = 824389441
```