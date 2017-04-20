[1]: http://rosettacode.org/wiki/Create_a_two-dimensional_array_at_runtime

# [Create a two-dimensional array at runtime][1]

```ruby
func make_matrix(x, y) {
    y.of { x.of(0) }
}
 
var y = read("rows: ", Number)
var x = read("cols: ", Number)
 
var matrix = make_matrix(x, y)    # create the matrix
matrix[y/2][x/2] = 1              # write something inside it
say matrix                        # display the matrix
```

#### Output:
```
rows: 3
cols: 4
[[0, 0, 0, 0], [0, 0, 1, 0], [0, 0, 0, 0]]
```
