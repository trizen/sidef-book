[1]: http://rosettacode.org/wiki/Combinations

# [Combinations][1]

#### Built-in
```ruby
combinations(5, 3, {|*c| say c })
```

#### Recursive

```ruby
func combine(n, set) {

    set.len || return []
    n == 1  && return set.map{[_]}

    var (head, result)
    head   = set.shift
    result = combine(n-1, [set...])

    for subarray in result {
        subarray.prepend(head)
    }

    result + combine(n, set)
}

combine(3, @^5).each {|c| say c }
```

#### Iterative

```ruby
func forcomb(callback, n, k) {

    if (k == 0) {
        callback([])
        return()
    }

    if (k<0 || k>n || n==0) {
        return()
    }

    var c = @^k

    loop {
        callback([c...])
        c[k-1]++ < n-1 && next
        var i = k-2
        while (i>=0 && c[i]>=(n-(k-i))) {
            --i
        }
        i < 0 && break
        c[i]++
        while (++i < k) {
            c[i] = c[i-1]+1
        }
    }

    return()
}

forcomb({|c| say c }, 5, 3)
```

#### Output

```ruby
[0, 1, 2]
[0, 1, 3]
[0, 1, 4]
[0, 2, 3]
[0, 2, 4]
[0, 3, 4]
[1, 2, 3]
[1, 2, 4]
[1, 3, 4]
[2, 3, 4]
```
