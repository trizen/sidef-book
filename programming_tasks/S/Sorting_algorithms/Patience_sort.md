[1]: https://rosettacode.org/wiki/Sorting_algorithms/Patience_sort

# [Sorting algorithms/Patience sort][1]

```ruby
func patience(deck) {
  var stacks = [];
  deck.each { |card|
    given (stacks.first { card < .last }) { |stack|
      case (defined stack) {
        stack << card
      }
      default {
        stacks << [card]
      }
    }
  }

  gather {
    while (stacks) {
      take stacks.min_by { .last }.pop
      stacks.grep!{ !.is_empty }
    }
  }
}

var a = [4, 65, 2, -31, 0, 99, 83, 782, 1]
say patience(a)
```

#### Output:
```
[-31, 0, 1, 2, 4, 65, 83, 99, 782]
```
