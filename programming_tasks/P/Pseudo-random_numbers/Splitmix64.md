[1]: https://rosettacode.org/wiki/Pseudo-random_numbers/Splitmix64

# [Pseudo-random numbers/Splitmix64][1]

```ruby
class Splitmix64(state) {
 
    define (
        mask64 = (2**64 - 1)
    )
 
    method next_int {
        var n = (state = ((state + 0x9e3779b97f4a7c15) & mask64))
        n = ((n ^ (n >> 30)) * 0xbf58476d1ce4e5b9 & mask64)
        n = ((n ^ (n >> 27)) * 0x94d049bb133111eb & mask64)
        (n ^ (n >> 31)) & mask64
    }
 
    method next_float {
        self.next_int / (mask64+1)
    }
}
 
say 'Seed: 1234567, first 5 values:'
var rng = Splitmix64(1234567)
5.of { rng.next_int.say }
 
say "\nSeed: 987654321, values histogram:"
var rng = Splitmix64(987654321)
var histogram = Bag(1e5.of { floor(5*rng.next_float) }...)
histogram.pairs.sort.each { .join(": ").say }
```

#### Output:
```
Seed: 1234567, first 5 values:
6457827717110365317
3203168211198807973
9817491932198370423
4593380528125082431
16408922859458223821

Seed: 987654321, values histogram:
0: 20027
1: 19892
2: 20073
3: 19978
4: 20030
```
