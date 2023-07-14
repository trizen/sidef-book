[1]: https://rosettacode.org/wiki/Detect_division_by_zero

# [Detect division by zero][1]

The numerical system of Sidef evaluates `x/0` to `+/-Inf`.

```ruby
func div_check(a, b){
    var result = a/b
    result.abs == Inf ? nil : result
}

say div_check(10, 2)  # 5
say div_check(1, 0)   # nil (detected)
```

Alternatively, we can do:

```ruby
func div_check(a, b){
    Perl.eval("#{a} / #{b}")
}

say div_check(10, 2)  # 5
say div_check(1, 0)   # nil (detected)
```
