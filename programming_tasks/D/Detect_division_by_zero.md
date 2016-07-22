[1]: http://rosettacode.org/wiki/Detect_division_by_zero

# [Detect division by zero][1]

```ruby
func div(a, b){
    var result = a/b
    result == Inf ? nil : result
}
 
say div(10, 2);      # 5
say div(1, 0);       # nil          (detected)
say div(1.c, 0.c);   # Inf+NaNi     (undetected)
```
