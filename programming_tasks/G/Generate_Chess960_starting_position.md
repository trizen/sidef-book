[1]: https://rosettacode.org/wiki/Generate_Chess960_starting_position

# [Generate Chess960 starting position][1]

```ruby
func is_valid_960 (backrank) {
    var king = backrank.index('♚')
    var (rook1, rook2) = backrank.indices_of('♜')...
    king.is_between(rook1, rook2) || return false
    var (bishop1, bishop2) = backrank.indices_of('♝')...
    bishop1+bishop2 -> is_odd
}
 
func random_960_position(pieces = <♛ ♚ ♜ ♜ ♝ ♝ ♞ ♞>) {
    pieces.shuffle.permutations {|*a|
        return a if is_valid_960(a)
    }
}
 
say random_960_position().join(' ')
```

#### Output:
```
♝ ♝ ♜ ♚ ♞ ♛ ♜ ♞
```
