[1]: http://rosettacode.org/wiki/Proper_divisors

# [Proper divisors][1]

```ruby
func propdiv (n) {
    gather {
        { |d|
            if (d `divides` n) {
                take(d, n//d)
            }
        } << 1..n.isqrt
    }.grep{ _ != n }.uniq.sort
}

{|i| say "#{i}\t#{propdiv(i)}" } << 1..10

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
