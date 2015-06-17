[1]: http://rosettacode.org/wiki/Man_or_boy_test

# [Man or boy test][1]

Sidef does not support closures, but something similar can be achieved by using the _Block.copy()_ method.

```ruby
func a(k, x1, x2, x3, x4, x5) {
    func b { (a.copy)(--k, b, x1, x2, x3, x4) };
    k <= 0 ? (x4() + x5()) : b();
};
println(a(10, {1}, {-1}, {-1}, {1}, {0}));      #=> -67
```