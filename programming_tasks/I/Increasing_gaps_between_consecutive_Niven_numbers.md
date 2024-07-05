[1]: https://rosettacode.org/wiki/Increasing_gaps_between_consecutive_Niven_numbers

# [Increasing gaps between consecutive Niven numbers][1]

```ruby
var threshold = 10_000_000

say "Gap    Index of gap  Starting Niven"
for (var (n=1, index=0, gap=0, prev=1); index <= threshold; ++n) {
    n.is_div(n.digits_sum) || next
    if ((var diff = (n - prev)) > gap) {
        gap = diff
        printf("%3d %15s %15s\n", gap, index, prev)
    }
    prev = n
    ++index
}
```

#### Output:
```
Gap    Index of gap  Starting Niven
  1               1               1
  2              10              10
  6              11              12
  7              26              63
  8              28              72
 10              32              90
 12              83             288
 14             102             378
 18             143             558
 23             561            2889
 32             716            3784
 36            1118            6480
 44            2948           19872
 45            4194           28971
 54            5439           38772
 60           33494          297864
 66           51544          478764
 72           61588          589860
 88           94748          989867
 90          265336         2879865
 99          800054         9898956
108         3750017        49989744
126         6292149        88996914
```
