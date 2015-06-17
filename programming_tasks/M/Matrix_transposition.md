[1]: http://rosettacode.org/wiki/Matrix_transposition

# [Matrix transposition][1]

```ruby
func transpose(matrix) {
    matrix[0].range.map{|i| matrix.map{_[i]}};
};
 
var m = [
  [1,  1,   1,   1],
  [2,  4,   8,  16],
  [3,  9,  27,  81],
  [4, 16,  64, 256],
  [5, 25, 125, 625],
];
 
transpose(m).each { |row|
    "%5d" * row.len -> printlnf(row...);
}
```

#### Output:
```
    1    2    3    4    5
    1    4    9   16   25
    1    8   27   64  125
    1   16   81  256  625
```