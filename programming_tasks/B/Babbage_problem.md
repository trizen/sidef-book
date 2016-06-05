[1]: http://rosettacode.org/wiki/Babbage_problem

# [Babbage problem][1]

```ruby
var n = 0
while (n*n % 1000000 != 269696) {
    n += 2
}
say n
```

#### Output:
```
25264
```