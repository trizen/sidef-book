[1]: https://rosettacode.org/wiki/Display_a_linear_combination

# [Display a linear combination][1]

```ruby
func linear_combination(coeffs) {
    var res = ""
    for e,f in (coeffs.kv) {
        given(f) {
            when (1) {
                res += "+e(#{e+1})"
            }
            when (-1) {
                res += "-e(#{e+1})"
            }
            case (.> 0) {
                res += "+#{f}*e(#{e+1})"
            }
            case (.< 0) {
                res += "#{f}*e(#{e+1})"
            }
        }
    }
    res -= /^\+/
    res || 0
}
 
var tests = [
    %n{1 2 3},
    %n{0 1 2 3},
    %n{1 0 3 4},
    %n{1 2 0},
    %n{0 0 0},
    %n{0},
    %n{1 1 1},
    %n{-1 -1 -1},
    %n{-1 -2 0 -3},
    %n{-1},
]
 
tests.each { |t|
    printf("%10s -> %-10s\n", t.join(' '), linear_combination(t))
}
```

#### Output:
```
     1 2 3 -> e(1)+2*e(2)+3*e(3)
   0 1 2 3 -> e(2)+2*e(3)+3*e(4)
   1 0 3 4 -> e(1)+3*e(3)+4*e(4)
     1 2 0 -> e(1)+2*e(2)
     0 0 0 -> 0         
         0 -> 0         
     1 1 1 -> e(1)+e(2)+e(3)
  -1 -1 -1 -> -e(1)-e(2)-e(3)
-1 -2 0 -3 -> -e(1)-2*e(2)-3*e(4)
        -1 -> -e(1)     
```