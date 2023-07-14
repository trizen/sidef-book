[1]: https://rosettacode.org/wiki/Chinese_remainder_theorem

# [Chinese remainder theorem][1]

```ruby
func chinese_remainder(*n) {
    var N = n.prod
    func (*a) {
        n.range.sum { |i|
            var p = (N / n[i])
            a[i] * p.invmod(n[i]) * p
        } % N
    }
}
 
say chinese_remainder(3, 5, 7)(2, 3, 2)
```

#### Output:
```
23
```
