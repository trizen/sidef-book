[1]: https://rosettacode.org/wiki/Pell's_equation

# [Pell's equation][1]

```ruby
func solve_pell(n) {
 
    var x = n.isqrt
    var y = x
    var z = 1
    var r = 2*x
 
    var (e1, e2) = (1, 0)
    var (f1, f2) = (0, 1)
 
    loop {
 
        y = (r*z - y)
        z = floor((n - y*y) / z)
        r = floor((x + y) / z)
 
        (e1, e2) = (e2, r*e2 + e1)
        (f1, f2) = (f2, r*f2 + f1)
 
        var A = (e2 + x*f2)
        var B = f2
 
        if (A**2 - n*B**2 == 1) {
            return (A, B)
        }
    }
}
 
for n in [61, 109, 181, 277] {
    var (x, y) = solve_pell(n)
    printf("x^2 - %3d*y^2 = 1 for x = %-21s and y = %s\n", n, x, y)
}
```

#### Output:
```
x^2 -  61*y^2 = 1 for x = 1766319049            and y = 226153980
x^2 - 109*y^2 = 1 for x = 158070671986249       and y = 15140424455100
x^2 - 181*y^2 = 1 for x = 2469645423824185801   and y = 183567298683461940
x^2 - 277*y^2 = 1 for x = 159150073798980475849 and y = 9562401173878027020
```