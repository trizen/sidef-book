[1]: http://rosettacode.org/wiki/Roots_of_a_quadratic_function

# [Roots of a quadratic function][1]

```ruby
var sets = [
            [1,    2,  1],
            [1,    2,  3],
            [1,   -2,  1],
            [1,    0, -4],
            [1, -1e6,  1],
           ];
 
func quadroots(a, b, c) {
    var root = (
        (b**2 - 4*a*c) -> complex.sqrt
    );
 
    a.complex!;
    b.complex!;
 
    [(-b + root) / (2 * a),
     (-b - root) / (2 * a)];
}
 
sets.each { |coefficients|
    say ("Roots for #{coefficients.dump}",
        "=> (#{quadroots(coefficients...).join(', ')})");
}
```

#### Output:
```
Roots for [1, 2, 1]=> (-1, -1)
Roots for [1, 2, 3]=> (-1+1.4142135623731i, -1-1.4142135623731i)
Roots for [1, -2, 1]=> (1, 1)
Roots for [1, 0, -4]=> (2, -2)
Roots for [1, -1000000, 1]=> (999999.999999, 1.00000761449337e-06)
```