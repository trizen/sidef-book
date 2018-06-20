[1]: https://rosettacode.org/wiki/Largest_number_divisible_by_its_digits

# [Largest number divisible by its digits][1]

```ruby
func largest_number(base) {
 
    var digits = @(base ^.. 1)
 
    digits.each {|k|
        digits.variations(k, {|*a|
            var n = Number(a.join, base)
            if (a.all {|d| d.divides(n) }) {
                return n
            }
        })
    }
}
 
say largest_number(10)   #=> 9867312
```