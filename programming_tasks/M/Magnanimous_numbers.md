[1]: https://rosettacode.org/wiki/Magnanimous_numbers

# [Magnanimous numbers][1]

```ruby
func is_magnanimous(n) {
    1..n.ilog10 -> all {|k|
        sum(divmod(n, k.ipow10)).is_prime
    }
}
 
say "First 45 magnanimous numbers:"
say is_magnanimous.first(45).join(' ')
 
say "\n241st through 250th magnanimous numbers:"
say is_magnanimous.first(250).last(10).join(' ')
 
say "\n391st through 400th magnanimous numbers:"
say is_magnanimous.first(400).last(10).join(' ')
```

#### Output:
```
First 45 magnanimous numbers:
0 1 2 3 4 5 6 7 8 9 11 12 14 16 20 21 23 25 29 30 32 34 38 41 43 47 49 50 52 56 58 61 65 67 70 74 76 83 85 89 92 94 98 101 110

241st through 250th magnanimous numbers:
17992 19972 20209 20261 20861 22061 22201 22801 22885 24407

391st through 400th magnanimous numbers:
486685 488489 515116 533176 551558 559952 595592 595598 600881 602081
```
