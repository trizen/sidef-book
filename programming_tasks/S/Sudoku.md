[1]: https://rosettacode.org/wiki/Sudoku

# [Sudoku][1]

```ruby
func check(i, j) is cached {
    var (id, im) = i.divmod(9)
    var (jd, jm) = j.divmod(9)

    jd == id && return true
    jm == im && return true

    (id//3 == jd//3) &&
    (jm//3 == im//3)
}

func solve(grid) {
    for i in ^grid {
        grid[i] && next
        var t = [grid[{|j| check(i, j) }.grep(^grid)]].freq

        { |k|
            t.has_key(k) && next
            grid[i] = k
            solve(grid)
        } << 1..9

        grid[i] = 0
        return nil
    }

    for i in ^grid {
        print "#{grid[i]} "
        print " "  if (3  -> divides(i+1))
        print "\n" if (9  -> divides(i+1))
        print "\n" if (27 -> divides(i+1))
    }
}

var grid = %i(
    5 3 0  0 2 4  7 0 0
    0 0 2  0 0 0  8 0 0
    1 0 0  7 0 3  9 0 2

    0 0 8  0 7 2  0 4 9
    0 2 0  9 8 0  0 7 0
    7 9 0  0 0 0  0 8 0

    0 0 0  0 3 0  5 0 6
    9 6 0  0 1 0  3 0 0
    0 5 0  6 9 0  0 1 0
)

solve(grid)
```

#### Output:
```
5 3 9  8 2 4  7 6 1
6 7 2  1 5 9  8 3 4
1 8 4  7 6 3  9 5 2

3 1 8  5 7 2  6 4 9
4 2 5  9 8 6  1 7 3
7 9 6  3 4 1  2 8 5

8 4 1  2 3 7  5 9 6
9 6 7  4 1 5  3 2 8
2 5 3  6 9 8  4 1 7
```
