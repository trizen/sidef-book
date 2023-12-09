[1]: https://rosettacode.org/wiki/LU_decomposition

# [LU decomposition][1]

```ruby
func is_square(m) { m.all { .len == m.len } }
func matrix_zero(n, m=n) { m.of { n.of(0) } }
func matrix_ident(n) { n.of {|i| [i.of(0)..., 1, (n - i - 1).of(0)...] } }

func pivotize(m) {
    var size = m.len
    var id = matrix_ident(size)
    for i in (^size) {
        var max = m[i][i]
        var row = i
        for j in (i ..^ size) {
            if (m[j][i] > max) {
                max = m[j][i]
                row = j
            }
        }
        if (row != i) {
            id.swap(row, i)
        }
    }
    return id
}

func mmult(a, b) {
    var p = []
    for r in ^a, c in ^b[0], i in ^b {
        p[r][c] := 0 += (a[r][i] * b[i][c])
    }
    return p
}

func lu(a) {
    is_square(a) || die "Defined only for square matrices!";
    var n = a.len
    var P = pivotize(a)
    var Aʼ = mmult(P, a)
    var L = matrix_ident(n)
    var U = matrix_zero(n)
    for i in ^n, j in ^n {
        if (j >= i) {
            U[i][j] = (Aʼ[i][j] - sum(^i, { U[_][j] * L[i][_] }))
        } else {
            L[i][j] = ((Aʼ[i][j] - sum(^j, { U[_][j] * L[i][_] })) / U[j][j])
        }
    }
    return [P, Aʼ, L, U]
}

func say_it(message, array) {
    say "\n#{message}"
    array.each { |row|
        say row.map{"%7s" % .as_rat}.join(' ')
    }
}

var t = [[
   %n(1 3 5),
   %n(2 4 7),
   %n(1 1 0),
],[
   %n(11  9 24  2),
   %n( 1  5  2  6),
   %n( 3 17 18  1),
   %n( 2  5  7  1),
]]

t.each { |test|
    say_it('A Matrix', test)
    for a,b in (['P Matrix', 'Aʼ Matrix', 'L Matrix', 'U Matrix'] ~Z lu(test)) {
        say_it(a, b)
    }
}
```

#### Output:
```
A Matrix
      1       3       5
      2       4       7
      1       1       0

P Matrix
      0       1       0
      1       0       0
      0       0       1

Aʼ Matrix
      2       4       7
      1       3       5
      1       1       0

L Matrix
      1       0       0
    1/2       1       0
    1/2      -1       1

U Matrix
      2       4       7
      0       1     3/2
      0       0      -2

A Matrix
     11       9      24       2
      1       5       2       6
      3      17      18       1
      2       5       7       1

P Matrix
      1       0       0       0
      0       0       1       0
      0       1       0       0
      0       0       0       1

Aʼ Matrix
     11       9      24       2
      3      17      18       1
      1       5       2       6
      2       5       7       1

L Matrix
      1       0       0       0
   3/11       1       0       0
   1/11   23/80       1       0
   2/11  37/160   1/278       1

U Matrix
     11       9      24       2
      0  160/11  126/11    5/11
      0       0 -139/40   91/16
      0       0       0  71/139
```
