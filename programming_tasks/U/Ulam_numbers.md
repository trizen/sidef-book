[1]: https://rosettacode.org/wiki/Ulam_numbers

# [Ulam numbers][1]

```ruby
func ulam(n) {
 
    static u     = Set(1,2)
    static ulams = [0, 1, 2]
 
    return ulams[n] if (ulams.end >= n)
 
    ++n
 
    for(var i = 3; true; ++i) {
        var count = 0
 
        ulams.each {|v|
            if (u.has(i - v) && (v != i-v)) {
                break if (count++ > 2)
            }
        }
 
        if (count == 2) {
            ulams << i
            u << i
            break if (ulams.len == n)
        }
    }
 
    ulams.tail
}
 
for k in (1..3) {
    say "The 10^#{k}-th Ulam number is: #{ulam(10**k)}"
}
```

#### Output:
```
The 10^1-th Ulam number is: 18
The 10^2-th Ulam number is: 690
The 10^3-th Ulam number is: 12294
```
