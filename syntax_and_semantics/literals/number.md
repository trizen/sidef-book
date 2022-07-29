# Numbers

```ruby
# Integers
say factorial(30)              #=> 265252859812191058636308480000000
say fibonacci(164)             #=> 8404037832974134882743767626780173

# Floating-point numbers
say sqrt(Num.pi)               #=> 1.7724538509055160272981674833[...]
say exp(1234)                  #=> 8.3059759373617942182585212913[...]e535

# Rational numbers
var x = 2/3
say x*3                        #=> 2
say 2/x                        #=> 3
say x.as_frac                  #=> 2/3

# Complex numbers
say Complex(3, 4)              #=> 3+4i
say 3+4.i                      #=> 3+4i
say sqrt(-4)                   #=> 2i
say log(-1)                    #=> 3.1415926535897932384626433832[...]i
```

The `Number` type (also aliased as `Num`) represents any Number object (including complex numbers):

```ruby
say 42.kind_of(Number)          #=> true
say sqrt(-1).kind_of(Number)    #=> true
```

Additionally, the `Number` class can be used for constructing new Number objects:

```ruby
Number("1234.52")         # set decimal number
Number("10110111", 2)     # set binary number
Number("deadbeef", 16)    # set hexadecimal number
```
