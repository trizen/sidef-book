[1]: https://rosettacode.org/wiki/Self-describing_numbers

# [Self-describing numbers][1]

```ruby
func sdn(Number n) {
    var b = [0]*n.len
    var a = n.digits.flip
    a.each { |i| b[i] := 0 ++ }
    a == b
}

var values = [1210, 2020, 21200, 3211000,
42101000, 521001000, 6210001000, 27, 115508]

values.each { |test|
    say "#{test} is #{sdn(test) ? '' : 'NOT ' }a self describing number."
}

say "\nSelf-descriptive numbers less than 1e5 (in base 10):"
{|i| say i if sdn(i) } << ^1e5
```

#### Output:
```
1210 is a self describing number.
2020 is a self describing number.
21200 is a self describing number.
3211000 is a self describing number.
42101000 is a self describing number.
521001000 is a self describing number.
6210001000 is a self describing number.
27 is NOT a self describing number.
115508 is NOT a self describing number.

Self-descriptive numbers less than 1e5 (in base 10):
1210
2020
21200
```


**Extra credit:** this will generate all the self-describing numbers in bases 7 to 36:

```ruby
for b in (7..36) {
    var n = ((b-4) * b**(b-1) + 2*(b**(b-2)) + b**(b-3) + b**3 -> base(b))
    say "base #{'%2d' % b}: #{n}"
}
```

#### Output:
```
base  7: 3211000
base  8: 42101000
base  9: 521001000
base 10: 6210001000
base 11: 72100001000
base 12: 821000001000
base 13: 9210000001000
base 14: a2100000001000
base 15: b21000000001000
base 16: c210000000001000
base 17: d2100000000001000
base 18: e21000000000001000
base 19: f210000000000001000
base 20: g2100000000000001000
base 21: h21000000000000001000
base 22: i210000000000000001000
base 23: j2100000000000000001000
base 24: k21000000000000000001000
base 25: l210000000000000000001000
base 26: m2100000000000000000001000
base 27: n21000000000000000000001000
base 28: o210000000000000000000001000
base 29: p2100000000000000000000001000
base 30: q21000000000000000000000001000
base 31: r210000000000000000000000001000
base 32: s2100000000000000000000000001000
base 33: t21000000000000000000000000001000
base 34: u210000000000000000000000000001000
base 35: v2100000000000000000000000000001000
base 36: w21000000000000000000000000000001000
```
