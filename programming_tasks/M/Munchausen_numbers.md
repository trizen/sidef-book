[1]: http://rosettacode.org/wiki/Munchausen_numbers

# [Munchausen numbers][1]

```ruby
func is_munchausen(n) {
    n.digits.map{|d| d**d }.sum == n
}
 
say (1..5000 -> grep(is_munchausen))
```

#### Output:
```
[1, 3435]
```