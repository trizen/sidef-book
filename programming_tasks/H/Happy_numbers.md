[1]: http://rosettacode.org/wiki/Happy_numbers

# [Happy numbers][1]

```ruby
func happy(n) is cached {
    static seen = Hash()

    return true  if n.is_one
    return false if seen.has_key(n)

    seen{n} = 1
    happy(n.digits »**» 2 -> sum)
}

var count = 0
Inf.times { |i|
    happy(i) ? say i : next
    ++count == 8 && break
}
```

#### Output:
```
1
7
10
13
19
23
28
31
```
