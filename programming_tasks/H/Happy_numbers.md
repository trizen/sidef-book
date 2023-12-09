[1]: https://rosettacode.org/wiki/Happy_numbers

# [Happy numbers][1]

```ruby
func happy(n) is cached {
    static seen = Hash()

    return true  if n.is_one
    return false if seen.exists(n)

    seen{n} = 1
    happy(n.digits.sum { _*_ })
}

say happy.first(10)
```

#### Output:
```
[1, 7, 10, 13, 19, 23, 28, 31, 32, 44]
```
