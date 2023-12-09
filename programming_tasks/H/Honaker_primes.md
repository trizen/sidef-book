[1]: https://rosettacode.org/wiki/Honaker_primes

# [Honaker primes][1]

```ruby
func is_honaker_prime (n) {
    n.is_prime && (n.sumdigits == n.prime_count.sumdigits)
}

say "The first 50 Honaker primes and their position:"
is_honaker_prime.first(50).each_slice(5, {|*slice|
    say ("%15s"*slice.len % slice.map{ [_, .prime_count] }...)
})

printf("\nHonaker prime 10000 is %s on position %s.\n",
    with (is_honaker_prime.nth(1e4)) {|k| (k, k.prime_count) })
```

#### Output:
```
The first 50 Honaker primes and their position:
      [131, 32]      [263, 56]      [457, 88]    [1039, 175]    [1049, 176]
    [1091, 182]    [1301, 212]    [1361, 218]    [1433, 227]    [1571, 248]
    [1913, 293]    [1933, 295]    [2141, 323]    [2221, 331]    [2273, 338]
    [2441, 362]    [2591, 377]    [2663, 386]    [2707, 394]    [2719, 397]
    [2729, 398]    [2803, 409]    [3067, 439]    [3137, 446]    [3229, 457]
    [3433, 481]    [3559, 499]    [3631, 508]    [4091, 563]    [4153, 571]
    [4357, 595]    [4397, 599]    [4703, 635]    [4723, 637]    [4903, 655]
    [5009, 671]    [5507, 728]    [5701, 751]    [5711, 752]    [5741, 755]
    [5801, 761]    [5843, 767]    [5927, 779]    [6301, 820]    [6311, 821]
    [6343, 826]    [6353, 827]    [6553, 847]    [6563, 848]    [6653, 857]

Honaker prime 10000 is 4043749 on position 286069.
```
