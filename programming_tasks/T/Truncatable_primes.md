[1]: https://rosettacode.org/wiki/Truncatable_primes

# [Truncatable primes][1]

```ruby
func t_prime(n, left=true) {
    var p = %w(2 3 5 7);
    var f = (
        left ? { '1'..'9' ~X+ p }
             : { p ~X+ '1'..'9' }
    )
    n.times {
        p = f().grep{ .to_i.is_prime }
    }
    p.map{.to_i}.max
}
 
say t_prime(5, left: true)
say t_prime(5, left: false)
```

#### Output:
```
998443
739399
```