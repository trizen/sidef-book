[1]: http://rosettacode.org/wiki/Perfect_shuffle

# [Perfect shuffle][1]

```ruby
func perfect_shuffle(deck) {
     deck/2 -> zip.flat
}

[8, 24, 52, 100, 1020, 1024, 10000].each { |size|
    var deck = @(1..size)
    var shuffled = deck

    var n = (1..Inf -> lazy.first {
        (shuffled = perfect_shuffle(shuffled)) == deck
    })

    printf("%5d cards: %4d\n", size, n)
}
```

#### Output:
```
    8 cards:    3
   24 cards:   11
   52 cards:    8
  100 cards:   30
 1020 cards: 1018
 1024 cards:   10
10000 cards:  300
```
