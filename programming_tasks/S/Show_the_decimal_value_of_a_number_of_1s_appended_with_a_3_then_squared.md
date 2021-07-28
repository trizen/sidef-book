[1]: https://rosettacode.org/wiki/Show_the_(decimal)_value_of_a_number_of_1s_appended_with_a_3,_then_squared

# [Show the (decimal) value of a number of 1s appended with a 3, then squared][1]

```ruby
0..^8 -> each {|n|
    var k = ((10**(n+1) - 1)/9 + 2)
    say [k, k**2]
}
```

#### Output:
```
[3, 9]
[13, 169]
[113, 12769]
[1113, 1238769]
[11113, 123498769]
[111113, 12346098769]
[1111113, 1234572098769]
[11111113, 123456832098769]
```
