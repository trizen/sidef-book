# Rational

Rational numbers are built-in, using [Math::GMPq](https://metacpan.org/pod/Math::GMPq), which provides a Perl interface to the `mpq` layer in the [GMP](https://gmplib.org/) library.

```ruby
3/4         # rational value: 3/4
2.5         # parsed and represented in rational form: 5/2
```

A numerical string can be converted into a rational number by using the `Number` class:

```ruby
Number("0.75")          # "0.75" is parsed and stored in rational form as 3/4
Number("fff/aaa", 36)   # parse a base-36 fraction as 4095/2730
```

The Number method `as_rat` can be used for getting the rational form of a number:

```ruby
say 3/4                # 0.75
say as_rat(3/4)        # 3/4
say as_rat(1.234, 36)  # h5/dw   (which is 617/500 in base-10)
```
