# Float

In Sidef, there is no real distinction between integers and floating-point numbers, as all numbers are represented by `Math::GMPq` in rational form.

```ruby
1.234;          # 1.234
.1234;          # 0.1234
1234e-5;        # 0.01234
12.34e5;        # 1234000
```
