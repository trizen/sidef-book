[1]: http://rosettacode.org/wiki/Linear_congruential_generator

# [Linear congruential generator][1]

```ruby
module LCG {
 
  # Creates a linear congruential generator with the given _seed_.
  class Common {
    -> new(seed) {
      self[:seed] = (self[:r] = seed);
    }
  }
 
  # LCG::Berkeley generates 31-bit integers using the same formula
  # as BSD rand().
  class Berkeley < Common {
    -> rand {
      self.r = ((1103515245 * self.r + 12345) & 0x7fff_ffff);
    }
  }
 
  # LCG::Microsoft generates 15-bit integers using the same formula
  # as rand() from the Microsoft C Runtime.
  class Microsoft < Common {
    -> rand {
      self.r = ((214013 * self.r + 2531011) & 0x7fff_ffff);
      self.r >> 16;
    }
  }
}
 
var lcg1 = LCG::Berkeley.new(1);
say 5.of { lcg1.rand };
 
var lcg2 = LCG::Microsoft.new(1);
say 5.of { lcg2.rand };
```

#### Output:
```
[1103527590, 377401575, 662824084, 1147902781, 2035015474]
[41, 18467, 6334, 26500, 19169]
```