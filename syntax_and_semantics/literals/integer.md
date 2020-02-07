# Integer literals

Sidef supports arbitarily large integers, by using [Math::GMPz](https://metacpan.org/pod/Math::GMPz), which is the Perl interface to the [GMP](https://gmplib.org/) library.

```ruby
255               # decimal
0xff              # hexadecimal
0377              # octal
0b1111_1111       # binary
```

A numerical string (in any base from 2 to 62) can be converted into a number as following:

```ruby
Number("1234")          # from string in base 10 (default)
Number("foo", 36)       # from string in base 36
```

The `Number.base(b)` method provides conversion from numbers into strings in a given base:

```ruby
1234.base(13)       # to string in base 13
1234.base(36)       # to string in base 36
```
