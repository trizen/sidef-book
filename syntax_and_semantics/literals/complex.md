# Complex

Support for complex numbers is provided by [Math::MPC](https://metacpan.org/pod/Math::MPC), which is a Perl interface to the [MPC](http://www.multiprecision.org/mpc/) library.

```ruby
Complex(3, 4)
```

Alternatively:

```ruby
3 + 4i
3:4
```

Complex numbers are deeply integrated into the language and can be used in combination with all the other Number types (with implicit propagation):

```ruby
sqrt(-1)        # 1i
log(-1)         # 3.14159265358979323846264338327950288419716939938i
4 + sqrt(-1)    # 4+i
(3+4i)**2       # -7+24i
```

All complex numbers are Number objects:

```ruby
(3 + 4i).class       # Number
Complex(3, 4).class  # =//=
```
