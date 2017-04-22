[1]: http://rosettacode.org/wiki/Remove_duplicate_elements

# [Remove duplicate elements][1]

```ruby
var ary = [1,1,2,1,'redundant',[1,2,3],[1,2,3],'redundant']
say ary.uniq
say ary.last_uniq
```

#### Output:
```
[1, 2, 'redundant', [1, 2, 3]]
[2, 1, [1, 2, 3], 'redundant']
```
