[1]: https://rosettacode.org/wiki/Perfect_totient_numbers

# [Perfect totient numbers][1]

```ruby
func perfect_totient({.<=1}, sum=0) { sum }
func perfect_totient(     n, sum=0) { __FUNC__(var(t = n.euler_phi), sum + t) }
 
say (1..Inf -> lazy.grep {|n| perfect_totient(n) == n }.first(20))
```

#### Output:
```
[3, 9, 15, 27, 39, 81, 111, 183, 243, 255, 327, 363, 471, 729, 2187, 2199, 3063, 4359, 4375, 5571]
```