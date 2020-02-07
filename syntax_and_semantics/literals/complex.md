# Complex literals

Support for complex numbers is provided by [Math::MPC](https://metacpan.org/pod/Math::MPC), which is a Perl interface to the [MPC](http://www.multiprecision.org/mpc/) library.

```ruby
3 + 4i          # complex: 3+4i
3:4             # =//=
Complex(3, 4)   # =//=
```

Complex numbers are deeply integrated into the language and can be used in combination with all the other Number types (with implicit propagation):

```ruby
sqrt(-1)        # i
log(-1)         # 3.14159265358979323846264338327950288419716939938i
4 + sqrt(-1)    # 4+i
(3+4i)**2       # -7+24i
```

All complex numbers are Number object:

```ruby
(3 + 4i).class       # Number
Complex(3, 4).class  # =//=
```

See the [Number](number.md) documentation for more information.
