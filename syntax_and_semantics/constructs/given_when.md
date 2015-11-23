# given/when

This is another construct borrowed from Perl 6 and it's almost the same as `switch/case` in most other languages.

```ruby
given (var value = 42) {
  when (value < 0) {
       say "Negative value!"
  }
  when (0) {
       say "Null value!"
  }
  when (1) {
       say "Value is: 1"
  }
  default {
       say "Value is greater than 1!"
  }
}
```
