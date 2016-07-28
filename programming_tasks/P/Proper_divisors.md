[1]: http://rosettacode.org/wiki/Proper_divisors

# [Proper divisors][1]

```ruby
func propdiv (x) {
    var divs = []
    divs << 1 if (x > 1)

    for d in (2 .. x.isqrt) {
        var y = (x // d)
        if (y*d == x) {
            divs << d
            y == d || (divs << y)
        }
    }

    divs
}

10.times { |i| say "#{i}\t#{propdiv(i)}" }

var max = 0
var candidates = []
20_000.times { |i|
    var divs = propdiv(i).len
    if (divs > max) {
        candidates = []
        max = divs
    }
    candidates << i if (divs == max)
}

say "max = #{max}, candidates = #{candidates}"
```

#### Output:
```
1       []
2       [1]
3       [1]
4       [1, 2]
5       [1]
6       [1, 2, 3]
7       [1]
8       [1, 2, 4]
9       [1, 3]
10      [1, 2, 5]
max = 79, candidates = [15120, 18480]
```
