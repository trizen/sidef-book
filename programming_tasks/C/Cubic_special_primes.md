[1]: https://rosettacode.org/wiki/Cubic_special_primes

# [Cubic special primes][1]

```ruby
func cubic_primes(callback) {
 
    var prev = 2
    callback(prev)
 
    loop {
        var curr = (1..Inf -> lazy.map { prev + _**3 }.first { .is_prime })
        callback(curr)
        prev = curr
    }
}
 
say gather {
    cubic_primes({|k|
        break if (k >= 15000)
        take(k)
    })
}
```

#### Output:
```
[2, 3, 11, 19, 83, 1811, 2027, 2243, 2251, 2467, 2531, 2539, 3539, 3547, 4547, 5059, 10891, 12619, 13619, 13627, 13691, 13907, 14419]
```
