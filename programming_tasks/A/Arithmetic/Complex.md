[1]: http://rosettacode.org/wiki/Arithmetic/Complex

# [Arithmetic/Complex][1]

```ruby
var a = 1:1                 # Complex(1, 1)
var b = 3.14159:1.25        # Complex(3.14159, 1.25)
 
[   a + b,                  # addition
    a * b,                  # multiplication
    -a,                     # negation
    a.inv,                  # multiplicative inverse
    a.conj,                 # complex conjugate
    a.abs,                  # abs
    a.sqrt,                 # sqrt
    b.re,                   # real
    b.im,                   # imaginary
].each { |c| say c }
```

#### Output:
```
4.14159+2.25i
1.89159+4.39159i
-1-i
0.5-0.5i
1-i
1.4142135623730950488016887242097
1.09868411346780996603980119524068+0.45508986056222734130435775782247i
3.14159
1.25
```
