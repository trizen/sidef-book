[1]: http://rosettacode.org/wiki/Arithmetic/Complex

# [Arithmetic/Complex][1]

```ruby
var a = 1:1;                # Complex(1, 1)
var b = 3.14159:1.25;       # Complex(3.14159, 1.25)
 
[   a + b,                  # addition
    a * b,                  # multiplication
    -a,                     # negation
    1c / a,                 # multiplicative inverse
    ~a,                     # complex conjugate
    a.abs,                  # abs
    a.sqrt.cartesian,       # sqrt
    b.re,                   # real
    b.im,                   # imaginary
].each { |c| say c };
```

#### Output:
```
4.14159+2.25i
1.89159+4.39159i
-1-i
0.5-0.5i
-2-i
1.4142135623731
1.09868411346781+0.455089860562227i
3.14159
1.25
```