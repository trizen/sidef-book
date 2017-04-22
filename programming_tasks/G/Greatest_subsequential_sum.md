[1]: http://rosettacode.org/wiki/Greatest_subsequential_sum

# [Greatest subsequential sum][1]

```ruby
func maxsubseq(*a) {
    var (start, end, sum, maxsum) = (-1, -1, 0, 0)
    a.each_kv { |i, x|
        sum += x
        if (maxsum < sum) {
            maxsum = sum
            end = i
        }
        elsif (sum < 0) {
            sum = 0
            start = i
        }
    }
    a.ft(start+1, end)
}
 
say maxsubseq(-1, -2,  3,  5,  6, -2, -1,  4, -4,  2, -1)
say maxsubseq(-2, -2, -1,  3,  5,  6, -1,  4, -4,  2, -1)
say maxsubseq(-2, -2, -1, -3, -5, -6, -1, -4, -4, -2, -1)
```

#### Output:
```
[3, 5, 6, -2, -1, 4]
[3, 5, 6, -1, 4]
[]
```
