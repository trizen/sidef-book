[1]: https://rosettacode.org/wiki/Sequence_of_non-squares

# [Sequence of non-squares][1]

```ruby
func nonsqr(n) { 0.5 + n.sqrt -> floor + n }
{|i| nonsqr(i) }.map(1..22).join(' ').say

{ |i|
  if (nonsqr(i).is_sqr) {
     die "Found a square in the sequence: #{i}"
  }
} << 1..1e6
```
