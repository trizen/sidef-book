[1]: https://rosettacode.org/wiki/Pascal's_triangle

# [Pascal's triangle][1]

```ruby
func pascal(rows) {
    var row = [1]
    { | n|
        say row.join(' ')
        row = [1, {|i| row[i] + row[i+1] }.map(0 .. n-2)..., 1]
    } << 1..rows
}
 
pascal(10)
```
