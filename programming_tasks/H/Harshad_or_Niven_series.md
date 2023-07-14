[1]: https://rosettacode.org/wiki/Harshad_or_Niven_series

# [Harshad or Niven series][1]

```ruby
func harshad() {
    var n = 0
    {
        ++n while !n.digits.sum.divides(n)
        n
    }
}
 
var iter = harshad()
say 20.of { iter.run }
 
var n
do {
    n = iter.run
} while (n <= 1000)
 
say n
```

#### Output:
```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 18, 20, 21, 24, 27, 30, 36, 40, 42]
1002
```
