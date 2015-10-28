[1]: http://rosettacode.org/wiki/Wireworld

# [Wireworld][1]

```ruby
var f = [[], DATA.lines.map {['', @.chomp.split(''), '']}..., []];
 
range(1, 10).each {
    say f.map { .join(" ") + "\n" }.join;
    var a = [[]];
    range(1, f.end-1).each { |y|
        var r = f[y];
        var rr = [''];
        range(1, r.end-1).each { |x|
            var c = r[x];
            rr.append(
              given(c) {
                when('H') { 't' }
                when('t') { '.' }
                when('.') { <. H>[f.ft(y-1, y+1).map{.ft(x-1, x+1)...}.count('H') ~~ [1,2]] }
                default   { c }
              }
            )
        }
        rr.append('');
        a.append(rr);
    }
    f = [a..., []];
}
 
__DATA__
tH.........
.   .
   ...
.   .
Ht.. ......
```