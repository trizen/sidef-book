[1]: http://rosettacode.org/wiki/Pythagorean_triples

# [Pythagorean triples][1]

```ruby
func triples(limit) {
    var primitive = 0;
    var civilized = 0;
 
    func oyako(a, b, c) {
        (var perim = a+b+c) > limit || (
            primitive++;
            civilized += int(limit / perim);
            oyako( a - 2*b + 2*c,  2*a - b + 2*c,  2*a - 2*b + 3*c);
            oyako( a + 2*b + 2*c,  2*a + b + 2*c,  2*a + 2*b + 3*c);
            oyako(-a + 2*b + 2*c, -2*a + b + 2*c, -2*a + 2*b + 3*c);
        );
    }
 
    oyako(3,4,5);
    "#{limit} => (#{primitive} #{civilized})";
}
 
range(1, Math.inf).each { |n|
    say triples(10**n);
};
```

#### Output:
```
10 => (0 0)
100 => (7 17)
1000 => (70 325)
10000 => (703 4858)
100000 => (7026 64741)
^C
```