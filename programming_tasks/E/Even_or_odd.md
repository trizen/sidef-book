[1]: https://rosettacode.org/wiki/Even_or_odd

# [Even or odd][1]

Built-in methods:

```ruby
var n = 42;
say n.is_odd;       # false
say n.is_even;      # true
```


Checking the last significant digit:

```ruby
func is_odd(n)  { n&1 == 1 };
func is_even(n) { n&1 == 0 };
```


Using modular congruences:

```ruby
func is_odd(n)  { n%2 == 1 };
func is_even(n) { n%2 == 0 };
```