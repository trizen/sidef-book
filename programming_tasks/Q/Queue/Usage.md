[1]: http://rosettacode.org/wiki/Queue/Usage

# [Queue/Usage][1]

```ruby
var f = FIFO()
say f.empty         # true
f.push('foo')
f.push('bar', 'baz')
say f.pop           # foo
say f.empty         # false
 
var g = FIFO('xxx', 'yyy')
say g.pop           # xxx
say f.pop           # bar
```
