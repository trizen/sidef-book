[1]: https://rosettacode.org/wiki/Write_float_arrays_to_a_text_file

# [Write float arrays to a text file][1]

```ruby
func writedat(filename, x, y, x_precision=3, y_precision=5) {
    var fh = File(filename).open_w
 
    for a,b in (x ~Z y) {
        fh.printf("%.*g\t%.*g\n", x_precision, a, y_precision, b)
    }
 
    fh.close
}
 
var x = [1, 2, 3, 1e11]
var y = x.map{.sqrt}
 
writedat('sqrt.dat', x, y)
```

#### Output:
```
1       1
2       1.4142
3       1.7321
1e+11   3.1623e+05
```
