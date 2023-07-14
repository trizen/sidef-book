[1]: https://rosettacode.org/wiki/Cycle_detection

# [Cycle detection][1]

```ruby
func brent (f, x0) {
    var power = 1
    var λ = 1
    var tortoise = x0
    var hare = f(x0)
 
    while (tortoise != hare) {
        if (power == λ) {
            tortoise = hare
            power *= 2
            λ = 0
        }
        hare = f(hare)
        λ += 1
    }
 
    var μ = 0
    tortoise = x0
    hare = x0
    { hare = f(hare) } * λ
 
    while (tortoise != hare) {
        tortoise = f(tortoise)
        hare = f(hare)
        μ += 1
    }
 
    return (λ, μ)
}
 
func cyclical_function(x) { (x*x + 1) % 255 }
 
var (l, s) = brent(cyclical_function, 3)
 
var seq = gather {
    var x = 3
    { take(x); x = cyclical_function(x) } * 20
}
 
say seq.join(', ')+', ...'
 
say "Cycle length #{l}.";
say "Cycle start index #{s}."
say [seq[s .. (s + l - 1)]]
```

#### Output:
```
3, 10, 101, 2, 5, 26, 167, 95, 101, 2, 5, 26, 167, 95, 101, 2, 5, 26, 167, 95, ...
Cycle length 6.
Cycle start index 2.
[101, 2, 5, 26, 167, 95]
```