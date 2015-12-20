# given/when

The `given/when` construct is borrowed from Perl 6 and it's somewhat equivalent with `switch/case` from other languages.

```ruby
given (42) {
  case (_ < 0) {
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

- `case` is used to test an expression for trueness
- `when` is used to test a value using the rules of the smartmarch operator

The rules of the smartmarch operator are pretty simple:

- `Obj ~~ Obj` will always check for equality when both objects have the same type.
- `Obj ~~ Array` will return true if `Obj` exists inside the array.
- `Obj ~~ Hash` will return true when `Obj` is a key inside the hash.
- `Obj ~~ Regex` will try to match the `Obj` against the regex and returns true on a successful match.
