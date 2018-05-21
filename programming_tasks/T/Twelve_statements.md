[1]: https://rosettacode.org/wiki/Twelve_statements

# [Twelve statements][1]

```ruby
var conditions = [
    { false },
    {|a| a.len == 13 },
    {|a| [a[7..12]].count(true) == 3 },
    {|a| [a[2..12 `by` 2]].count(true) == 2 },
    {|a| a[5] ? (a[6] && a[7]) : true },
    {|a| !a[2] && !a[3] && !a[4] },
    {|a| [a[1..11 `by` 2]].count(true) == 4 },
    {|a| a[2] == true^a[3] },
    {|a| a[7] ? (a[5] && a[6]) : true },
    {|a| [a[1..6]].count(true)  == 3 },
    {|a| [a[11,12]].count(true) == 2 },
    {|a| [a[7..9]].count(true)  == 1 },
    {|a| [a[1..11]].count(true) == 4 },
]

func miss(args) {
    1..12 -> grep {|i| conditions[i](args) != args[i] }
}

for k in (^(1<<12)) {
  var t  = ("0%012b" % k -> chars.map {|bit| bit == '1' })
  var no = miss(t)
  no.len == 0 && say "Solution: true statements are #{1..12->grep{t[_]}.join(' ')}"
  no.len == 1 && say "1 miss (#{no[0]}): true statements are #{1..12->grep{t[_]}.join(' ')}"
}
```

#### Output:
```
1 miss (1): true statements are 5 8 11
1 miss (1): true statements are 5 8 10 11 12
1 miss (1): true statements are 4 8 10 11 12
1 miss (8): true statements are 1 5
1 miss (11): true statements are 1 5 8
1 miss (12): true statements are 1 5 8 11
1 miss (12): true statements are 1 5 8 10 11 12
1 miss (8): true statements are 1 5 6 9 11
1 miss (8): true statements are 1 4
1 miss (12): true statements are 1 4 8 10 11 12
1 miss (6): true statements are 1 4 6 8 9
1 miss (7): true statements are 1 3 4 8 9
Solution: true statements are 1 3 4 6 7 11
1 miss (9): true statements are 1 3 4 6 7 9
1 miss (12): true statements are 1 2 4 7 9 12
1 miss (10): true statements are 1 2 4 7 9 10
1 miss (8): true statements are 1 2 4 7 8 9
```
