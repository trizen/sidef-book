[1]: https://rosettacode.org/wiki/Pseudo-random_numbers/PCG32

# [Pseudo-random numbers/PCG32][1]

```ruby
class PCG32(seed, incr) {
 
    has state
 
    define (
        mask32 = (2**32 - 1),
        mask64 = (2**64 - 1),
        N      = 6364136223846793005,
    )
 
    method init {
        seed := 1
        incr := 2
        incr  = (((incr << 1) | 1) & mask64)
        state = (((incr + seed)*N + incr) & mask64)
    }
 
    method next_int {
        var shift  = ((((state >> 18) ^ state) >> 27) & mask32)
        var rotate = ((state >> 59) & mask32)
            state  = ((state*N + incr) & mask64)
        ((shift >> rotate) | (shift << (32-rotate))) & mask32
    }
 
    method next_float {
        self.next_int / (mask32+1)
    }
}
 
say "Seed: 42, Increment: 54, first 5 values:";
var rng = PCG32(seed: 42, incr: 54)
say 5.of { rng.next_int }
 
say "\nSeed: 987654321, Increment: 1, values histogram:";
var rng = PCG32(seed: 987654321, incr: 1)
var histogram = Bag(1e5.of { floor(5*rng.next_float) }...)
histogram.pairs.sort.each { .join(": ").say }
```

#### Output:
```
Seed: 42, Increment: 54, first 5 values:
[2707161783, 2068313097, 3122475824, 2211639955, 3215226955]

Seed: 987654321, Increment: 1, values histogram:
0: 20049
1: 20022
2: 20115
3: 19809
4: 20005
```
