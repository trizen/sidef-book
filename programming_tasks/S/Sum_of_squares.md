[1]: http://rosettacode.org/wiki/Sum_of_squares

# [Sum of squares][1]

```ruby
func sum_of_squares(vector) {
    var sum = 0
    vector.each { |n| sum += n**2 }
    return sum
}
 
say sum_of_squares([])          # 0
say sum_of_squares([1,2,3])     # 14
```
