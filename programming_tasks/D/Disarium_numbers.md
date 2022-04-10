[1]: https://rosettacode.org/wiki/Disarium_numbers

# [Disarium numbers][1]

```ruby
func is_disarium(n) {
    n.digits.flip.sum_kv{|k,d| d**(k+1) } == n
}
 
say 18.by(is_disarium)
```

#### Output:
```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 89, 135, 175, 518, 598, 1306, 1676, 2427]
```
