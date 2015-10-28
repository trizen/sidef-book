[1]: http://rosettacode.org/wiki/Permutations

# [Permutations][1]

Built-in:

```ruby
[1,2,3].permutations { |set|
    say set.join;
}
```


Iterative:

```ruby
func permutations(callback, arr) {
    var end = arr.end;
    var idx = 0..end;
 
    loop {
        callback([arr.@[idx]]);
 
        var p = end;
        while (idx[p-1] > idx[p]) {p--};
        p == 0 && return;
 
        var d = p;
        idx += idx.splice(p).reverse;
 
        while (idx[p-1] > idx[d]) {d++};
        idx[p-1, d] = idx[d, p-1];
    }
}
 
var list = [1,2,3];
permutations({|set| say set.join }, list);
```


Recursive:

```ruby
func permutations(callback, set, perm=[]) {
    set.is_empty && callback(perm);
    set.range.each { |i|
        __FUNC__(callback, [set[@(0 .. i-1), @(i+1 .. set.end)]], [perm..., set[i]]);
    }
}
 
var list = [1,2,3];
permutations({|set| say set.join}, list);
```

#### Output:
```
123
132
213
231
312
321
```