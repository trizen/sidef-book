[1]: http://rosettacode.org/wiki/Queue/Definition

# [Queue/Definition][1]

Implemented as a class:

```ruby
class FIFO(*array) {
    method pop {
        array.is_empty && die "underflow";
        array.shift;
    }
    method push(*items) {
        array += items;
        self;
    }
    method empty {
        array.len == 0;
    }
}
```


Usage:

```ruby
var f = FIFO();
say f.empty;        # true
f.push('foo');
f.push('bar', 'baz');
say f.pop;          # foo
say f.empty;        # false
 
var g = FIFO('xxx', 'yyy');
say g.pop;          # xxx
say f.pop;          # bar
```