[1]: http://rosettacode.org/wiki/Odd_word_problem

# [Odd word problem][1]

Recursive solution:

```ruby
func rev {
    (var c = STDIN.getc) \\ return()
    if (c ~~ /^[a-z]\z/i) {
        var r = rev()
        print c
        return r
    }
    return c
}
 
var (n=0, l=false)
while (defined(var c = STDIN.getc)) {
    var w = (c ~~ /^[a-z]\z/i)
    ++n if (w && !l)
    l = w
    if (n & 1) {
        print c
    } else {
        var r = rev()
        print(c, r)
        n = 0
        l = false
    }
}
```

#### Output:
```
$ echo 'what,is,the;meaning,of:life.' | sidef script.sf
what,si,the;gninaem,of:efil.

$ echo 'we,are;not,in,kansas;any,more.' | sidef script.sf
we,era;not,ni,kansas;yna,more.
```