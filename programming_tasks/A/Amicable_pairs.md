[1]: http://rosettacode.org/wiki/Amicable_pairs

# [Amicable pairs][1]

```ruby
func propdivsum(x) {
    gather {
        2.to(x.isqrt).each { |d|
            if (x %% d) {
                take(d)
                take(x/d) if !x.is_sqr
            }
        }
    }.sum(x > 0 ? 1 : 0)
}
 
1.to(20000).each { |i|
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