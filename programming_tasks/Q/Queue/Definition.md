[1]: http://rosettacode.org/wiki/Queue/Definition

# [Queue/Definition][1]

Implemented as a class:

```ruby
class FIFO(*array) {
    method pop {
        array.is_empty && die "underflow"
        array.shift
    }
    method push(*items) {
        array += items
        self
    }
    method empty {
        array.len == 0
    }
}
```
