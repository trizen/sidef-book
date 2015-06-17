[1]: http://rosettacode.org/wiki/Matrix_multiplication

# [Matrix multiplication][1]

```ruby
func matrix_multi(a, b) {
    var m = [[]];
    a.range.each { |r|
        b.first.range.each { |c|
            b.range.each { |i|
                m[r][c] := 0 += (a[r][i] * b[i][c]);
            }
        }
    };
    return m;
};
 
var a = [
          [1, 2],
          [3, 4],
          [5, 6],
          [7, 8]
        ];
 
var b = [
          [1, 2, 3],
          [4, 5, 6]
        ];
 
matrix_multi(a, b).each {|line|
    say line.map{|i|'%3d'.sprintf(i)}.join(', ');
};
```

#### Output:
```
  9,  12,  15
 19,  26,  33
 29,  40,  51
 39,  54,  69
```