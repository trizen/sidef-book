[1]: https://rosettacode.org/wiki/Least_common_multiple

# [Least common multiple][1]

Built-in:

```ruby
say Math.lcm(1001, 221)
```


Using GCD:

```ruby
func gcd(a, b) {
    while (a) { (a, b) = (b % a, a) }
    return b
}
 
func lcm(a, b) {
    (a && b) ? (a / gcd(a, b) * b) : 0
}
 
say lcm(1001, 221)
```

#### Output:
```
17017
```