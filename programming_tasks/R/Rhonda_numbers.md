[1]: https://rosettacode.org/wiki/Rhonda_numbers

# [Rhonda numbers][1]

```ruby
func is_rhonda_number(n, base = 10) {
    base.is_composite || return false
    n > 0             || return false
    n.digits(base).prod == base*n.factor.sum
}
 
for b in (2..16 -> grep { .is_composite }) {
    say ("First 10 Rhonda numbers to base #{b}: ",
        10.by { is_rhonda_number(_, b) })
}
```

#### Output:
```
First 10 Rhonda numbers to base 4: [10206, 11935, 12150, 16031, 45030, 94185, 113022, 114415, 191149, 244713]
First 10 Rhonda numbers to base 6: [855, 1029, 3813, 5577, 7040, 7304, 15104, 19136, 35350, 36992]
First 10 Rhonda numbers to base 8: [1836, 6318, 6622, 10530, 14500, 14739, 17655, 18550, 25398, 25956]
First 10 Rhonda numbers to base 9: [15540, 21054, 25331, 44360, 44660, 44733, 47652, 50560, 54944, 76857]
First 10 Rhonda numbers to base 10: [1568, 2835, 4752, 5265, 5439, 5664, 5824, 5832, 8526, 12985]
First 10 Rhonda numbers to base 12: [560, 800, 3993, 4425, 4602, 4888, 7315, 8296, 9315, 11849]
First 10 Rhonda numbers to base 14: [11475, 18655, 20565, 29631, 31725, 45387, 58404, 58667, 59950, 63945]
First 10 Rhonda numbers to base 15: [2392, 2472, 11468, 15873, 17424, 18126, 19152, 20079, 24388, 30758]
First 10 Rhonda numbers to base 16: [1000, 1134, 6776, 15912, 19624, 20043, 20355, 23946, 26296, 29070]
```
