[1]: https://rosettacode.org/wiki/Factor-perfect_numbers

# [Factor-perfect numbers][1]

```ruby
func erdosFactorCount (n) is cached {

    var sum = 1
    var divs = proper_divisors(n).slice(1)

    divs.each {|d|
        sum += __FUNC__(idiv(n,d))
    }

    return sum
}

func moreMultiples (to, from) {
    var oneMores = []
    from.each {|j|
        if (j > to.tail && to.tail.divides(j)) {
            oneMores << [to..., j]
        }
    }
    for k in (oneMores.range) {
        oneMores << __FUNC__(oneMores[k], from)...
    }
    return oneMores
}

var listing = [[1]]
listing << moreMultiples([1], proper_divisors(48))...
listing.each {|a| a << 48 }

say "#{listing.len} sequences using first definition:"
listing.slices(3).each { .map { .join(' ') }.map{ '%-20s' % _ }.join.say }

var listing2 = gather {
    for j in (^listing.len) {
        var seq = listing[j]
        take(1..seq.end -> map {|j| seq[j] / seq[j-1] })
    }
}

say "\n#{listing2.len} sequences using second definition:"
listing2.slices(3).each { .map { .join(' ') }.map{ '%-20s' % _ }.join.say }

print "\nOEIS A163272: "
say [0, 1, (1..Inf -> lazy.map {|n| 4*n }.grep{|n| erdosFactorCount(n) == n }.first(5))...]
```

#### Output:
```
48 sequences using first definition:
1 48                1 2 48              1 3 48
1 4 48              1 6 48              1 8 48
1 12 48             1 16 48             1 24 48
1 2 4 48            1 2 6 48            1 2 8 48
1 2 12 48           1 2 16 48           1 2 24 48
1 2 4 8 48          1 2 4 12 48         1 2 4 16 48
1 2 4 24 48         1 2 4 8 16 48       1 2 4 8 24 48
1 2 4 12 24 48      1 2 6 12 48         1 2 6 24 48
1 2 6 12 24 48      1 2 8 16 48         1 2 8 24 48
1 2 12 24 48        1 3 6 48            1 3 12 48
1 3 24 48           1 3 6 12 48         1 3 6 24 48
1 3 6 12 24 48      1 3 12 24 48        1 4 8 48
1 4 12 48           1 4 16 48           1 4 24 48
1 4 8 16 48         1 4 8 24 48         1 4 12 24 48
1 6 12 48           1 6 24 48           1 6 12 24 48
1 8 16 48           1 8 24 48           1 12 24 48

48 sequences using second definition:
48                  2 24                3 16
4 12                6 8                 8 6
12 4                16 3                24 2
2 2 12              2 3 8               2 4 6
2 6 4               2 8 3               2 12 2
2 2 2 6             2 2 3 4             2 2 4 3
2 2 6 2             2 2 2 2 3           2 2 2 3 2
2 2 3 2 2           2 3 2 4             2 3 4 2
2 3 2 2 2           2 4 2 3             2 4 3 2
2 6 2 2             3 2 8               3 4 4
3 8 2               3 2 2 4             3 2 4 2
3 2 2 2 2           3 4 2 2             4 2 6
4 3 4               4 4 3               4 6 2
4 2 2 3             4 2 3 2             4 3 2 2
6 2 4               6 4 2               6 2 2 2
8 2 3               8 3 2               12 2 2

OEIS A163272: [0, 1, 48, 1280, 2496, 28672, 29808]
```
