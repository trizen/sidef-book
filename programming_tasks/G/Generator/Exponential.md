[1]: https://rosettacode.org/wiki/Generator/Exponential

# [Generator/Exponential][1]

```ruby
func gen_pow(m) {
    var e = 0;
    func { e++ ** m };
}
 
func gen_filter(g1, g2) {
    var v2 = g2.run;
    func {
        loop {
            var v1 = g1.run;
            while (v1 > v2) { v2 = g2.run };
            v1 == v2 || return v1;
        }
    }
}
 
# Create generators.
var squares = gen_pow(2);
var cubes = gen_pow(3);
var squares_without_cubes = gen_filter(squares, cubes);
 
# Drop 20 values.
20.times { squares_without_cubes() };
 
# Print 10 values.
var answer = [];
10.times { answer.append(squares_without_cubes()) };
say answer;
```

#### Output:
```
[529, 576, 625, 676, 784, 841, 900, 961, 1024, 1089]
```