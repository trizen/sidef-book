[1]: https://rosettacode.org/wiki/Knight's_tour

# [Knight's tour][1]

```ruby
var board = []
var I = 8
var J = 8
var F = (I*J > 99 ? '%3d' : '%2d')
 
var (i, j) = (I.irand, J.irand)
 
func from_algebraic(square) {
     if (var match = square.match(/^([a-z])([0-9])\z/)) {
         return(I - Num(match[1]), match[0].ord - 'a'.ord)
     }
     die "Invalid block square: #{square}"
}
 
func possible_moves(i,j) {
    gather {
        for ni,nj in [
            [i-2,j-1], [i-2,j+1], [i-1,j-2], [i-1,j+2],
            [i+1,j-2], [i+1,j+2], [i+2,j-1], [i+2,j+1],
        ] {
            if ((ni ~~ ^I) && (nj ~~ ^J) && !board[ni][nj]) {
                take([ni, nj])
            }
        }
    }
}
 
func to_algebraic(i,j) {
    ('a'.ord + j).chr + Str(I - i)
}
 
if (ARGV[0]) {
    (i, j) = from_algebraic(ARGV[0])
}
 
var moves = []
for move in (1 .. I*J) {
    moves << to_algebraic(i, j)
    board[i][j] = move
    var min = [9]
    for target in possible_moves(i, j) {
        var (ni, nj) = target...
        var nxt = possible_moves(ni, nj).len
        if (nxt < min[0]) {
            min = [nxt, ni, nj]
        }
    }
 
    (i, j) = min[1,2]
}
 
say (moves/4 -> map { .join(', ') }.join("\n") + "\n")
 
for i in ^I {
    for j in ^J {
        (i%2 == j%2) && print "\e[7m"
        F.printf(board[i][j])
        print "\e[0m"
    }
    print "\n"
}
```