[1]: http://rosettacode.org/wiki/Identity_matrix

# [Identity matrix][1]

```ruby
func identity_matrix(n) {
    n.of { |i|
        n.of { |j|
            i == j ? 1 : 0
        }
    }
}

for n (ARGV ? ARGV.map{.to_i} : [4, 5, 6]) {
  say "\n#{n}:"
  for row (identity_matrix(n)) {
    say row.join(' ')
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
