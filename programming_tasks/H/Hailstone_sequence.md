[1]: https://rosettacode.org/wiki/Hailstone_sequence

# [Hailstone sequence][1]

```ruby
func hailstone (n) {
    var sequence = [n]
    while (n > 1) {
        sequence << (
            n.is_even ? n.div!(2)
                      : n.mul!(3).add!(1)
        )
    }
    return(sequence)
}
 
# The hailstone sequence for the number 27
var arr = hailstone(var nr = 27)
say "#{nr}: #{arr.first(4)} ... #{arr.last(4)} (#{arr.len})"
 
# The longest hailstone sequence for a number less than 100,000
var h = [0, 0]
for i (1 .. 99_999) {
    (var l = hailstone(i).len) > h[1] && (
        h = [i, l]
    )
}
 
printf("%d: (%d)\n", h...)
```
