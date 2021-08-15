[1]: https://rosettacode.org/wiki/Pseudo-random_numbers/Combined_recursive_generator_MRG32k3a

# [Pseudo-random numbers/Combined recursive generator MRG32k3a][1]

```ruby
class MRG32k3a(seed) {
 
    define(
        m1 = (2**32 - 209)
        m2 = (2**32 - 22853)
    )
 
    define(
        a1 = %n<     0 1403580  -810728>
        a2 = %n<527612       0 -1370589>
    )
 
    has x1 = [seed, 0, 0]
    has x2 = x1.clone
 
    method next_int {
        x1.unshift(a1.map_kv {|k,v| v * x1[k] }.sum % m1); x1.pop
        x2.unshift(a2.map_kv {|k,v| v * x2[k] }.sum % m2); x2.pop
        (x1[0] - x2[0]) % (m1 + 1)
    }
 
    method next_float { self.next_int / (m1 + 1) -> float }
}
 
say "Seed: 1234567, first 5 values:"
var rng = MRG32k3a(seed: 1234567)
5.of { rng.next_int }.each { .say }
 
say "\nSeed: 987654321, values histogram:";
var rng = MRG32k3a(seed: 987654321)
var freq = 100_000.of { rng.next_float * 5 -> int }.freq
freq.sort.each_2d {|k,v| say "#{k} #{v}" }
```

#### Output:
```
Seed: 1234567, first 5 values:
1459213977
2827710106
4245671317
3877608661
2595287583

Seed: 987654321, values histogram:
0 20002
1 20060
2 19948
3 20059
4 19931
```
