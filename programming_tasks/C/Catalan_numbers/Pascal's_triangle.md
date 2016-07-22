[1]: http://rosettacode.org/wiki/Catalan_numbers/Pascal's_triangle

# [Catalan numbers/Pascal's triangle][1]

```ruby
func catalan(num) {
  var t = [0, 1]
  1..num -> map { |i|
    ::range(i, 1, -1).each {|j| t[j] += t[j-1]}
    t[i+1] = t[i]
    ::range(i+1, 1, -1).each {|j| t[j] += t[j-1]}
    t[i+1] - t[i]
  }
}

say catalan(15).join(' ')
```

#### Output:
```
1 2 5 14 42 132 429 1430 4862 16796 58786 208012 742900 2674440 9694845
```
