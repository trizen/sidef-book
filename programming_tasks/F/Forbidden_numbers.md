[1]: https://rosettacode.org/wiki/Forbidden_numbers

# [Forbidden numbers][1]

```ruby
say ("First 50 terms: ", 50.by { .squares_r(3) == 0 })

for n in (500, 5_000, 50_000, 500_000) {
    var v = (1..n -> count {|n|
        idiv(n, ipow(4, n.valuation(4))).is_congruent(7, 8)
    })
    say "There are #{v} forbidden numbers up to #{n.commify}."
}
```

#### Output:
```
First 50 terms: [7, 15, 23, 28, 31, 39, 47, 55, 60, 63, 71, 79, 87, 92, 95, 103, 111, 112, 119, 124, 127, 135, 143, 151, 156, 159, 167, 175, 183, 188, 191, 199, 207, 215, 220, 223, 231, 239, 240, 247, 252, 255, 263, 271, 279, 284, 287, 295, 303, 311]
There are 82 forbidden numbers up to 500.
There are 831 forbidden numbers up to 5,000.
There are 8330 forbidden numbers up to 50,000.
There are 83331 forbidden numbers up to 500,000.
```
