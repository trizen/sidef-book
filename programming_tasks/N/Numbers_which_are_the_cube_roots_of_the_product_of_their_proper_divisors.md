[1]: https://rosettacode.org/wiki/Numbers_which_are_the_cube_roots_of_the_product_of_their_proper_divisors

# [Numbers which are the cube roots of the product of their proper divisors][1]

```ruby
say ("First 50 terms: ", 50.by { .proper_divisors.prod == .cube }.join(' '))

for n in (5e2, 5e3, 5e4) {
    say "#{'%6s'%n.commify}th term: #{n.th{ .proper_divisors.prod == .cube }}"
}
```

#### Output:
```
First 50 terms: 1 24 30 40 42 54 56 66 70 78 88 102 104 105 110 114 128 130 135 136 138 152 154 165 170 174 182 184 186 189 190 195 222 230 231 232 238 246 248 250 255 258 266 273 282 285 286 290 296 297
   500th term: 2526
 5,000th term: 23118
50,000th term: 223735
```
