# Float literals

In Sidef, all literal numbers are specially parsed and converted implicitly into a rational number, which are internally represented by [Math::GMPz](https://metacpan.org/pod/Math::GMPz) and [Math::GMPq](https://metacpan.org/pod/Math::GMPq).

```ruby
1.234           # 1.234
.1234           # 0.1234
1234e-5         # 0.01234
12.34e5         # 1234000
```

This means that Sidef, by default, does not suffer from the [floating-point inaccuracy](https://0.30000000000000004.com/):

```ruby
0.1 + 0.2 == 0.3    # true
```

An integer or a rational number can be converted to a floating-point value by using the `.float` Number method, which represents floating-points using [Math::MPFR](https://metacpan.org/pod/Math::MPFR) (which is the Perl interface to the [MPFR](https://www.mpfr.org/) library) at a default precision of 192 bits:

```ruby
1.234.float         # conversion to floating-point number
```

In numerical operations, a floating-point number will automatically propagate:

```ruby
var x = 3/4         # rational
var y = 0.9.float   # floating-point
var z = x+y         # floating-point
```


The precision of floating-point numbers can be changed by modifying the `Num!PREC` class-variable:

```ruby
say sqrt(2)          # 1.41421356237309504880168872420969807856967187538
local Num!PREC = 24  # number of bits of precision
say sqrt(2)          # 1.41421
```

By using the `local` keyword, the precision will be changed only locally (which also includes any function/method call in the current scope):

```ruby
func my_sqrt(n) {
    sqrt(n)
}

say my_sqrt(2)              # 1.41421356237309504880168872420969807856967187538

do {                        # creates a new scope
    local Num!PREC = 24     # changes the floating-point precision locally
    say my_sqrt(2)          # 1.41421
}                           # the default precision is restored when the scope ends

say my_sqrt(2)              # 1.41421356237309504880168872420969807856967187538
```
