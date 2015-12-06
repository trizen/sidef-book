[1]: http://rosettacode.org/wiki/Ackermann_function

# [Ackermann function][1]

```ruby
func A(m, n) {
    m == 0 ? (n + 1)
           : (n == 0 ? (A(m - 1, 1))
                     : (A(m - 1, A(m, n - 1))));
}
```

Alternatively, using multiple dispatch:

```ruby
func A((0), n) { n + 1 }
func A(m, (0)) { A(m - 1, 1) }
func A(m,  n)  { A(m-1, A(m, n-1)) }
```

Calling the function:

```ruby
say A(3, 2);     # prints: 29
```
