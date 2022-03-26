[1]: https://rosettacode.org/wiki/Quadrat_special_primes

# [Quadrat special primes][1]

```ruby
func quadrat_primes(callback) {
 
    var prev = 2
    callback(prev)
 
    loop {
        var curr = (1..Inf -> lazy.map { prev + _**2 }.first { .is_prime })
        callback(curr)
        prev = curr
    }
}
 
say gather {
    quadrat_primes({|k|
        break if (k >= 16000)
        take(k)
    })
}
```

#### Output:
```
[2, 3, 7, 11, 47, 83, 227, 263, 587, 911, 947, 983, 1019, 1163, 1307, 1451, 1487, 1523, 1559, 2459, 3359, 4259, 4583, 5483, 5519, 5843, 5879, 6203, 6779, 7103, 7247, 7283, 7607, 7643, 8219, 8363, 10667, 11243, 11279, 11423, 12323, 12647, 12791, 13367, 13691, 14591, 14627, 14771, 15671]
```
