[1]: http://rosettacode.org/wiki/Gaussian_elimination

# [Gaussian elimination][1]

```ruby
var Matrix = require('Math::Matrix');
 
var a = Matrix.new([0,1,0],
                   [0,0,1],
                   [2,0,1]);
 
var b = Matrix.new([1],
                   [2],
                   [4]);
 
a.concat(b).solve.print;
```

#### Output:
```
   1.00000 
   1.00000 
   2.00000 
```