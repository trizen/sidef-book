[1]: http://rosettacode.org/wiki/Identity_matrix

# [Identity matrix][1]

```ruby
func identity_matrix(n) {
    1..n -> map { |i|
        1..n -> map {|j| j == i ? 1 : 0 }
    }
}
 
(ARGV.len ? ARGV.map{.to_i} : [4, 5, 6]) -> each { |n|
  say "\n#{n}:";
  identity_matrix(n).each { |row|
    say row.join(' ');
  }
}
```

#### Output:
```
4:
1 0 0 0
0 1 0 0
0 0 1 0
0 0 0 1

5:
1 0 0 0 0
0 1 0 0 0
0 0 1 0 0
0 0 0 1 0
0 0 0 0 1

6:
1 0 0 0 0 0
0 1 0 0 0 0
0 0 1 0 0 0
0 0 0 1 0 0
0 0 0 0 1 0
0 0 0 0 0 1
```