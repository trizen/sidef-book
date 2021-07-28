[1]: https://rosettacode.org/wiki/Getting_the_number_of_decimals

# [Getting the number of decimals][1]

```ruby
func number_of_decimals(n, limit = 1e5) {
    var prec = Num(Num!PREC)>>2
    var prev = ''
 
    n = Number(n) if !n.kind_of(Number)
 
    loop {
        var str = n.as_dec(prec)
 
        if (prev == str) {
            return (str.contains('.') ? str.substr(str.index('.')+1).len : 0)
        }
 
        prev = str
        prec *= 2
        return Inf if (prec > limit)
    }
}
 
var list = [
    9, 12.345, "12.3450", "12.345e53",
    12.34555555555555555555, 0.1234567890987654321,
    Num.pi, 1/3, 1.5**63
]
 
list.each {|n|
    var c = number_of_decimals(n)
    say "Number of decimals: #{'%3s' % c}  Number: #{n}"
}
```

#### Output:
```
Number of decimals:   0  Number: 9
Number of decimals:   3  Number: 12.345
Number of decimals:   3  Number: 12.3450
Number of decimals:   0  Number: 12.345e53
Number of decimals:  20  Number: 12.34555555555555555555
Number of decimals:  19  Number: 0.1234567890987654321
Number of decimals: 188  Number: 3.14159265358979323846264338327950288419716939938
Number of decimals: Inf  Number: 0.333333333333333333333333333333333333333333333333
Number of decimals:  63  Number: 124093581919.6489476978273736503801880082242803382541751489
```
