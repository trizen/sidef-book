[1]: https://rosettacode.org/wiki/Pseudo-random_numbers/Xorshift_star

# [Pseudo-random numbers/Xorshift star][1]

```ruby
class Xorshift_star(state) {
 
    define (
        mask32 = (2**32 - 1),
        mask64 = (2**64 - 1),
    )
 
    method next_int {
        state ^= (state >> 12)
        state ^= (state << 25 & mask64)
        state ^= (state >> 27)
        (state * 0x2545F4914F6CDD1D) >> 32 & mask32
    }
 
    method next_float {
        self.next_int / (mask32+1)
    }
}
 
say 'Seed: 1234567, first 5 values:';
var rng = Xorshift_star(1234567)
say 5.of { rng.next_int }
 
say "\nSeed: 987654321, values histogram:";
var rng = Xorshift_star(987654321)
var histogram = Bag(1e5.of { floor(5*rng.next_float) }...)
histogram.pairs.sort.each { .join(": ").say }
```

#### Output:
```
Seed: 1234567, first 5 values:
[3540625527, 2750739987, 4037983143, 1993361440, 3809424708]

Seed: 987654321, values histogram:
0: 20103
1: 19922
2: 19937
3: 20031
4: 20007
```
