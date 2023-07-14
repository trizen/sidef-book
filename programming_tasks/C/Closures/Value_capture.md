[1]: https://rosettacode.org/wiki/Closures/Value_capture

# [Closures/Value capture][1]

```ruby
var f = (
    10.of {|i| func(j){i * j} }
)

9.times { |j|
    say f[j](j)
}
```

#### Output:
```
0
1
4
9
16
25
36
49
64
```


Starting from i=1:

```ruby
var f = (1..10).map { |i|
    func(j){i * j}
}

for j (1..9) {
    say f[j-1](j)
}
```

#### Output:
```
1
4
9
16
25
36
49
64
81
```
