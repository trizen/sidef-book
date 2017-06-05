[1]: https://rosettacode.org/wiki/Permutations_with_repetitions

# [Permutations with repetitions][1]

```ruby
var k = %w(a b c)
var n = 2
 
cartesian([k] * n, {|*a| say a.join(' ') })
```

#### Output:
```
a a
a b
a c
b a
b b
b c
c a
c b
c c
```