[1]: https://rosettacode.org/wiki/Abundant,_deficient_and_perfect_number_classifications

# [Abundant, deficient and perfect number classifications][1]

```ruby
func propdivsum(n) {
    n.sigma - n
}
 
var h = Hash()
{|i| ++(h{propdivsum(i) <=> i} := 0) } << 1..20000
say "Perfect: #{h{0}}    Deficient: #{h{-1}}    Abundant: #{h{1}}"
```

#### Output:
```
Perfect: 4    Deficient: 15043    Abundant: 4953
```
