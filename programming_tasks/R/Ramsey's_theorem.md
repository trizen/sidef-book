[1]: http://rosettacode.org/wiki/Ramsey's_theorem

# [Ramsey's theorem][1]

```ruby
var a = 17.of { 17.of(0) }

17.itimes{|i| a[i][i] = '-' }
4.itimes { |k|
  17.itimes { |i|
    var j = ((i + 1<<k) % 17)
    a[i][j] = (a[j][i] = 1)
  }
}

a.each {|row| say row.join(' ') }

@(0..16).combinations(4).each { |quartet|
  var links = quartet.combinations(2).map{|p| a.dig(p...) }.sum
  ((0 < links) && (links < 6)) || die "Bogus!"
}
say "Ok"
```

#### Output:
```
- 1 1 0 1 0 0 0 1 1 0 0 0 1 0 1 1
1 - 1 1 0 1 0 0 0 1 1 0 0 0 1 0 1
1 1 - 1 1 0 1 0 0 0 1 1 0 0 0 1 0
0 1 1 - 1 1 0 1 0 0 0 1 1 0 0 0 1
1 0 1 1 - 1 1 0 1 0 0 0 1 1 0 0 0
0 1 0 1 1 - 1 1 0 1 0 0 0 1 1 0 0
0 0 1 0 1 1 - 1 1 0 1 0 0 0 1 1 0
0 0 0 1 0 1 1 - 1 1 0 1 0 0 0 1 1
1 0 0 0 1 0 1 1 - 1 1 0 1 0 0 0 1
1 1 0 0 0 1 0 1 1 - 1 1 0 1 0 0 0
0 1 1 0 0 0 1 0 1 1 - 1 1 0 1 0 0
0 0 1 1 0 0 0 1 0 1 1 - 1 1 0 1 0
0 0 0 1 1 0 0 0 1 0 1 1 - 1 1 0 1
1 0 0 0 1 1 0 0 0 1 0 1 1 - 1 1 0
0 1 0 0 0 1 1 0 0 0 1 0 1 1 - 1 1
1 0 1 0 0 0 1 1 0 0 0 1 0 1 1 - 1
1 1 0 1 0 0 0 1 1 0 0 0 1 0 1 1 -
Ok
```
