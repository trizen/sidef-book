[1]: http://rosettacode.org/wiki/Wireworld

# [Wireworld][1]

```ruby
var f = [[], DATA.lines.map {['', .chars..., '']}..., []]

10.times {
    say f.map { .join(" ") + "\n" }.join
    var a = [[]]
    for y in (1 ..^ f.end) {
        var r = f[y]
        var rr = ['']
        for x in (1 ..^ r.end) {
            var c = r[x]
            rr << (
              given(c) {
                when('H') { 't' }
                when('t') { '.' }
                when('.') { <. H>[f.ft(y-1, y+1).map{.ft(x-1, x+1)...}.count('H') ~~ [1,2]] }
                default   { c }
              }
            )
        }
        rr << ''
        a << rr
    }
    f = [a..., []]
}

__DATA__
tH.........
.   .
   ...
.   .
Ht.. ......
```
