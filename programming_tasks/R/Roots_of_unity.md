[1]: http://rosettacode.org/wiki/Roots_of_unity

# [Roots of unity][1]

```ruby
func roots_of_unity (n) {
    n.of { |j|
        exp(2.i * Complex.pi / n * (j-1))
    }
}
 
roots_of_unity(5).each { |c|
    printf("%+.5f%+.5fi\n", c.reals);
}
```

#### Output:
```
+1.00000+0.00000i
+0.30902+0.95106i
-0.80902+0.58779i
-0.80902-0.58779i
+0.30902-0.95106i
```
```ruby
5.times { |n|
    var roots = Complex(1).roots(n);
    printf ("%2d. ", n);
    say roots.map{ "%+.5f%+.5fi" % .reals }.join(' ');
}
```

#### Output:
```
 1. +1.00000+0.00000i
 2. +1.00000+0.00000i -1.00000+0.00000i
 3. +1.00000+0.00000i -0.50000+0.86603i -0.50000-0.86603i
 4. +1.00000+0.00000i +0.00000+1.00000i -1.00000+0.00000i -0.00000-1.00000i
 5. +1.00000+0.00000i +0.30902+0.95106i -0.80902+0.58779i -0.80902-0.58779i +0.30902-0.95106i
```