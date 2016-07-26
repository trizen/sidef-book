[1]: http://rosettacode.org/wiki/Hofstadter-Conway_$10,000_sequence

# [Hofstadter-Conway $10,000 sequence][1]

```ruby
class HofstadterConway10000 {
  has sequence = [nil, 1, 1]

  method term(n {.is_pos}) {
    var a = sequence
    a.len .. n -> each {|i| a[i] = a[a[i-1]]+a[i-a[i-1]] }
    a[n]
  }
}

var hc = HofstadterConway10000()

var mallows = nil
for i in (1..19) {
  var j = i+1
  var (max_n, max_v) = (-1, -1)
  for n in (1<<i .. 1<<j) {
    var v = (hc.term(n) / n)
    (max_n, max_v) = (n, v) if (v > max_v)
    mallows = n if (v >= 0.55)
  }
  say ("maximum between 2^%2d and 2^%2d occurs at%7d: %.8f" % (i, j, max_n, max_v))
}

say "the mallows number is #{mallows}"
```

#### Output:
```
maximum between 2^ 1 and 2^ 2 occurs at      3: 0.66666667
maximum between 2^ 2 and 2^ 3 occurs at      6: 0.66666667
maximum between 2^ 3 and 2^ 4 occurs at     11: 0.63636364
maximum between 2^ 4 and 2^ 5 occurs at     23: 0.60869565
maximum between 2^ 5 and 2^ 6 occurs at     44: 0.59090909
maximum between 2^ 6 and 2^ 7 occurs at     92: 0.57608696
maximum between 2^ 7 and 2^ 8 occurs at    178: 0.56741573
maximum between 2^ 8 and 2^ 9 occurs at    370: 0.55945946
maximum between 2^ 9 and 2^10 occurs at    719: 0.55493741
maximum between 2^10 and 2^11 occurs at   1487: 0.55010087
maximum between 2^11 and 2^12 occurs at   2897: 0.54746289
maximum between 2^12 and 2^13 occurs at   5969: 0.54414475
maximum between 2^13 and 2^14 occurs at  11651: 0.54244271
maximum between 2^14 and 2^15 occurs at  22223: 0.54007110
maximum between 2^15 and 2^16 occurs at  45083: 0.53878402
maximum between 2^16 and 2^17 occurs at  89516: 0.53704366
maximum between 2^17 and 2^18 occurs at 181385: 0.53602007
maximum between 2^18 and 2^19 occurs at 353683: 0.53464543
maximum between 2^19 and 2^20 occurs at 722589: 0.53377923
the mallows number is 1489
```
