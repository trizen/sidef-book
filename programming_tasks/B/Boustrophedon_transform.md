[1]: https://rosettacode.org/wiki/Boustrophedon_transform

# [Boustrophedon transform][1]

```ruby
func boustrophedon_transform(seq) {
    func T(k,n) is cached {
        return seq[k] if (n == 0)
        T(k, n-1) + T(k-1, k-n)
    }
    var bt = seq.range.map {|n| T(n,n) }
    T.uncache
    return bt
}

const N = 100   # n terms

[
    '1 followed by 0\'s A000111', Math.seq(1,{0}),
    'All-1\'s           A000667', Math.seq({1}),
    '(-1)^n             A062162', Math.seq({|_,k| (-1)**(k+1) }),
    'Primes             A000747', Math.seq(2,{ .tail.next_prime }),
    'Fibbonaccis        A000744', Math.seq(1,1,{ .last(2).sum }),
    'Factorials         A230960', Math.seq(1,{|a,k| a.last * (k-1) }),
].each_slice(2, {|name, seq|
    var bt = boustrophedon_transform(seq.first(N))
    say "\n#{name}:\n#{bt.first(15).join(' ')}"
    var v = bt[N-1]
    say ("#{N}th term: ", Str(v).first(20), '..', Str(v).last(20), " (%s digits)" % v.len)
})
```

#### Output:
```
1 followed by 0's A000111:
1 1 1 2 5 16 61 272 1385 7936 50521 353792 2702765 22368256 199360981
100th term: 45608516616801111821..68991870306963423232 (137 digits)

All-1's           A000667:
1 2 4 9 24 77 294 1309 6664 38177 243034 1701909 13001604 107601977 959021574
100th term: 21939873756450413339..30507739683220525509 (138 digits)

(-1)^n             A062162:
1 0 0 1 0 5 10 61 280 1665 10470 73621 561660 4650425 41441530
100th term: 94810791122872999361..65519440121851711941 (136 digits)

Primes             A000747:
2 5 13 35 103 345 1325 5911 30067 172237 1096319 7677155 58648421 485377457 4326008691
100th term: 98967625721691921699..78027927576425134967 (138 digits)

Fibbonaccis        A000744:
1 2 5 14 42 144 563 2526 12877 73778 469616 3288428 25121097 207902202 1852961189
100th term: 42390820205259437020..42168748587048986542 (138 digits)

Factorials         A230960:
1 2 5 17 73 381 2347 16701 134993 1222873 12279251 135425553 1627809401 21183890469 296773827547
100th term: 31807659526053444023..65546706672657314921 (157 digits)
```
