[1]: http://rosettacode.org/wiki/Binary_digits

# [Binary digits][1]

```ruby
[5, 50, 9000].each { |n|
    say n.to_bin.substr(2);
}
```

#### Output:
```
101
110010
10001100101000
```