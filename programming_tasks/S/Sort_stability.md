[1]: http://rosettacode.org/wiki/Sort_stability

# [Sort stability][1]

Sidef uses the stable merge-sort algorithm for sorting an array.

```ruby
var table = [
  <UK  London>,
  <US  New\ York>,
  <US  Birmingham>,
  <UK  Birmingham>,
]
 
table.sort {|a,b| a[0] <=> b[0] }.each { |col|
    say "#{col[0]} #{col[1]}"
}
```

#### Output:
```
UK London
UK Birmingham
US New York
US Birmingham
```
