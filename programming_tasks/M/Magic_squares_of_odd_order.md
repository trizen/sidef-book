[1]: http://rosettacode.org/wiki/Magic_squares_of_odd_order

# [Magic squares of odd order][1]

```ruby
func magic_square(n {.is_pos && .is_odd}) {
    var i = 0
    var j = int(n/2)

    var magic_square = []
    for l in (1 .. n**2) {
        magic_square[i][j] = l

        if (magic_square[i.dec % n][j.inc % n]) {
            i = (i.inc % n)
        }
        else {
            i = (i.dec % n)
            j = (j.inc % n)
        }
    }

    return magic_square
}

func print_square(sq) {
    var f = "%#{(sq.len**2).len}d";
    for row in sq {
        say row.map{ f % _ }.join(' ')
    }
}

var(n=5) = ARGV»to_i»()...
var sq = magic_square(n)
print_square(sq)

say "\nThe magic number is: #{sq[0].sum}"
```

#### Output:
```
17 24  1  8 15
23  5  7 14 16
 4  6 13 20 22
10 12 19 21  3
11 18 25  2  9

The magic number is: 65
```
