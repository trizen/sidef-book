[1]: http://rosettacode.org/wiki/Roots_of_unity

# [Roots of unity][1]

```ruby
func roots_of_unity(n) {
    n.of { |j|
        exp(2.i * Num.pi / n * (j-1))
    }
}

for c in (roots_of_unity(5)) {
    printf("%+.5f%+.5fi\n", c.reals)
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
