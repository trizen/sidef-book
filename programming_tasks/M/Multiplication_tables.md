[1]: http://rosettacode.org/wiki/Multiplication_tables

# [Multiplication tables][1]

```ruby
var max = 12;
var width = (max**2 -> len+1);
 
func fmt_row(*items) {
    items.map { |s| "%*s" % (width, s) }.join('');
}
 
say fmt_row('x┃', (1..max)...);
say "#{'━' * (width - 1)}╋#{'━' * (max * width)}";
 
max.times { |i|
    say fmt_row("#{i}┃", max.of {|j| i <= j ? i*j : ''}...);
}
```

#### Output:
```
  x┃   1   2   3   4   5   6   7   8   9  10  11  12
━━━╋━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  1┃   1   2   3   4   5   6   7   8   9  10  11  12
  2┃       4   6   8  10  12  14  16  18  20  22  24
  3┃           9  12  15  18  21  24  27  30  33  36
  4┃              16  20  24  28  32  36  40  44  48
  5┃                  25  30  35  40  45  50  55  60
  6┃                      36  42  48  54  60  66  72
  7┃                          49  56  63  70  77  84
  8┃                              64  72  80  88  96
  9┃                                  81  90  99 108
 10┃                                     100 110 120
 11┃                                         121 132
 12┃                                             144
```
