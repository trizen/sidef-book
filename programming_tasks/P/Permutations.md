[1]: http://rosettacode.org/wiki/Permutations

# [Permutations][1]


#### Built-in

```ruby
[1,2,3].permutations { |p|
    say p
}
```


#### Iterative

```ruby
func forperm(callback, n) {
    var idx = @^n

    loop {
        callback(idx...)

        var p = n-1
        while (idx[p-1] > idx[p]) {--p}
        p == 0 && return()

        var d = p
        idx += idx.splice(p).reverse

        while (idx[p-1] > idx[d]) {++d}
        idx.swap(p-1, d)
    }

    return()
}

forperm({|*p| say p }, 3)
```


#### Recursive

```ruby
func permutations(callback, set, perm=[]) {
    set || callback(perm)
    for i in ^set {
        __FUNC__(callback, [
            set[^i, i+1 ..^ set.len]
        ], [perm..., set[i]])
    }
    return()
}

permutations({|p| say p }, [0,1,2])
```


#### Output:

```
[0, 1, 2]
[0, 2, 1]
[1, 0, 2]
[1, 2, 0]
[2, 0, 1]
[2, 1, 0]
```
