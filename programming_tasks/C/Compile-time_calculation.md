[1]: http://rosettacode.org/wiki/Compile-time_calculation

# [Compile-time calculation][1]

The compile-time evaluation is limited at a constant expression, which cannot refer at any other user-defined data, such as variables or functions.

```ruby
define n = (10!);
say n;
```


or:

```ruby
define n = (func(n){ n > 0 ? __FUNC__(n-1)*n : 1 }(10));
say n;
```