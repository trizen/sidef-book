[1]: https://rosettacode.org/wiki/List_rooted_trees

# [List rooted trees][1]

```ruby
func bagchain(x, n, bb, start=0) {
    n || return [x]

    var out = []
    for i in (start .. bb.end) {
        var (c, s) = bb[i]...
        if (c <= n) {
            out += bagchain([x[0] + c, x[1] + s], n-c, bb, i)
        }
    }

    return out
}

func bags(n) {
    n || return [[0, ""]]
    var upto = []
    for i in (n ^.. 1) { upto += bags(i) }
    bagchain([0, ""], n-1, upto).map{|p| [p[0]+1, '('+p[1]+')'] }
}

func replace_brackets(s) {
    var (depth, out) = (0, [])
    for c in s {
        if (c == '(') {
            out.append(<( [ {>[depth%3])
            ++depth
        }
        else {
            --depth
            out.append(<) ] }>[depth%3])
        }
    }
    return out.join
}

for x in (bags(5)) {
    say replace_brackets(x[1])
}
```

#### Output:
```
([{([])}])
([{()()}])
([{()}{}])
([{}{}{}])
([{()}][])
([{}{}][])
([{}][{}])
([{}][][])
([][][][])
```
