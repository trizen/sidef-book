[1]: https://rosettacode.org/wiki/Amicable_pairs

# [Amicable pairs][1]

```ruby
func propdivsum(n) {
    n.sigma - n
}

for i in (1..20000) {
    var j = propdivsum(i)
    say "#{i} #{j}" if (j>i && i==propdivsum(j))
}
```

#### Output:
```
220 284
1184 1210
2620 2924
5020 5564
6232 6368
10744 10856
12285 14595
17296 18416
```
