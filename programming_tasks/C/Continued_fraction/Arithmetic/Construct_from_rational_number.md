[1]: https://rosettacode.org/wiki/Continued_fraction/Arithmetic/Construct_from_rational_number

# [Continued fraction/Arithmetic/Construct from rational number][1]

```ruby
func r2cf(num, den) {
    func() {
        den || return nil
        var q = num//den
        (num, den) = (den, num - q*den)
        return q
    }
}
 
func showcf(f) {
    print "["
    var n = f()
    print "#{n}" if defined(n)
    print "; #{n}" while defined(n = f())
    print "]\n"
}
 
[
    [1/2, 3/1, 23/8, 13/11, 22/7, -151/77],
    [14142/10000, 141421/100000, 1414214/1000000, 14142136/10000000],
    [314285714/100000000],
].each { |seq|
    seq.each { |r| showcf(r2cf(r.nude)) }
    print "\n"
}
```

#### Output:
```
[0; 2]
[3]
[2; 1; 7]
[1; 5; 2]
[3; 7]
[-1; -1; -24; -1; -2]

[1; 2; 2; 2; 2; 2; 1; 1; 29]
[1; 2; 2; 2; 2; 2; 2; 3; 1; 1; 3; 1; 7; 2]
[1; 2; 2; 2; 2; 2; 2; 2; 3; 6; 1; 2; 1; 12]
[1; 2; 2; 2; 2; 2; 2; 2; 2; 2; 6; 1; 2; 4; 1; 1; 2]

[3; 7; 7142857]
```
