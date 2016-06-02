[1]: http://rosettacode.org/wiki/Integer_roots

# [Integer roots][1]

```ruby
func root(a, b) {
    b < 2 && return(b)
    var (a1, c) = (a-1, 1)
    var f = {|x| (a1*x + b//(x**a1)) // a }
    var d = f(c)
    var e = f(d)
    while (c !~ [d, e]) {
        (c, d, e) = (d, e, f(e))
    }
    [d, e].min
}
 
say "First 2,001 digits of the square root of two:"
say root(2, 2 * 100**2000)
```

#### Output:
```
First 2,001 digits of the square root of two:
14142135623730950488016887242096980[...]32952546758516447107578486024636008
```