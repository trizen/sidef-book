[1]: https://rosettacode.org/wiki/Circles_of_given_radius_through_two_points

# [Circles of given radius through two points][1]

```ruby
func circles(a, b, r) {
 
    if (a == b) {
        if (r == 0) {
            return ['Degenerate point']
        }
        else {
            return ['Infinitely many share a point']
        }
    }
 
    var h = (b-a)/2
 
    if (r**2 < h.norm) {
        return ['Too far apart']
    }
 
    var l = sqrt(r**2 - h.norm)
 
    [1i, -1i].map {|i|
        a + h + (l*i*h / h.abs) -> round(-16)
    }
}
 
var input = [
    [0.1234 + 0.9876i,  0.8765 + 0.2345i, 2.0],
    [0.0000 + 2.0000i,  0.0000 + 0.0000i, 1.0],
    [0.1234 + 0.9876i,  0.1234 + 0.9876i, 2.0],
    [0.1234 + 0.9876i,  0.8765 + 0.2345i, 0.5],
    [0.1234 + 0.9876i,  0.1234 + 0.9876i, 0.0],
]
 
input.each {|a|
    say (a.join(', '), ': ', circles(a...).join(' and '))
}
```

#### Output:
```
0.1234+0.9876i, 0.8765+0.2345i, 2: 1.8631118016581891+1.9742118016581891i and -0.8632118016581891-0.7521118016581891i
2i, 0, 1: i and i
0.1234+0.9876i, 0.1234+0.9876i, 2: Infinitely many share a point
0.1234+0.9876i, 0.8765+0.2345i, 0.5: Too far apart
0.1234+0.9876i, 0.1234+0.9876i, 0: Degenerate point
```