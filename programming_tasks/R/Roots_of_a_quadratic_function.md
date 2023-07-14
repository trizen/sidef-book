[1]: https://rosettacode.org/wiki/Roots_of_a_quadratic_function

# [Roots of a quadratic function][1]

```ruby
var sets = [
            [1,    2,  1],
            [1,    2,  3],
            [1,   -2,  1],
            [1,    0, -4],
            [1, -1e6,  1],
           ]

func quadroots(a, b, c) {
    var root = sqrt(b**2 - 4*a*c)

    [(-b + root) / (2 * a),
     (-b - root) / (2 * a)]
}

sets.each { |coefficients|
    say ("Roots for #{coefficients}",
        "=> (#{quadroots(coefficients...).join(', ')})")
}
```

#### Output:
```
Roots for [1, 2, 1]=> (-1, -1)
Roots for [1, 2, 3]=> (-1+1.41421356237309504880168872420969807856967187538i, -1-1.41421356237309504880168872420969807856967187538i)
Roots for [1, -2, 1]=> (1, 1)
Roots for [1, 0, -4]=> (2, -2)
Roots for [1, -1000000, 1]=> (999999.999998999999999998999999999997999999999995, 0.00000100000000000100000000000200000000000500000000002)
```
