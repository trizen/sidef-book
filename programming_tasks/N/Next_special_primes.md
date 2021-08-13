[1]: https://rosettacode.org/wiki/Next_special_primes

# [Next special primes][1]

```ruby
func special_primes(upto) {
 
    var gap  = 0
    var prev = 2
    var list = [[prev, gap]]
 
    loop {
        var n = prev+gap
        n = n.next_prime
        break if (n > upto)
        gap = n-prev
        list << [n, gap]
        prev = n
    }
 
    return list
}
 
special_primes(1050).each_2d {|p,gap|
    say "#{'%4s' % p} #{'%4s' % gap}"
}
```

#### Output:
```
   2    0
   3    1
   5    2
  11    6
  19    8
  29   10
  41   12
  59   18
  79   20
 101   22
 127   26
 157   30
 191   34
 227   36
 269   42
 313   44
 359   46
 409   50
 461   52
 521   60
 587   66
 659   72
 733   74
 809   76
 887   78
 967   80
1049   82
```
