[1]: http://rosettacode.org/wiki/Reduced_row_echelon_form

# [Reduced row echelon form][1]

```ruby
func rref (Array m) {
    m.is_empty && return nil;
    var (lead, rows, cols) = (0, m.len, m[0].len);

    for r in ^rows {
        lead >= cols && return m;
        var i = r;

        while (!m[i][lead]) {
            ++i == rows || next;
            i = r;
            ++lead == cols && return m;
        }

        m[i, r] = m[r, i];
        var lv = m[r][lead];
        m[r] = (m[r] »/» lv);

        for n in ^rows {
            n == r && next;
            m[n] = (m[n] »-« (m[r] «*« m[n][lead]))
        }
        ++lead;
    }
    return m
}

func say_it (message, array) {
    say "\n#{message}";
    for row in array {
        say row.map { |n| " %5s" % n.as_rat }.join
    }
}

var M = [
    [ # base test case
      [  1,  2,  -1,  -4 ],
      [  2,  3,  -1, -11 ],
      [ -2,  0,  -3,  22 ],
    ],
    [ # mix of number styles
      [  3,   0,  -3,    1 ],
      [ .5, 3/2,  -3,   -2 ],
      [ .2, 4/5,  -1.6, .3 ],
    ],
    [ # degenerate case
      [ 1,  2,  3,  4,  3,  1],
      [ 2,  4,  6,  2,  6,  2],
      [ 3,  6, 18,  9,  9, -6],
      [ 4,  8, 12, 10, 12,  4],
      [ 5, 10, 24, 11, 15, -4],
    ],
];

M.each { |matrix|
    say_it('Original Matrix', matrix);
    say_it('Reduced Row Echelon Form Matrix', rref(matrix));
    say '';
}
```

#### Output:
```
Original Matrix
     1     2    -1    -4
     2     3    -1   -11
    -2     0    -3    22

Reduced Row Echelon Form Matrix
     1     0     0    -8
     0     1     0     1
     0     0     1    -2


Original Matrix
     3     0    -3     1
   1/2   3/2    -3    -2
   1/5   4/5  -8/5  3/10

Reduced Row Echelon Form Matrix
     1     0     0 -41/2
     0     1     0 -217/6
     0     0     1 -125/6


Original Matrix
     1     2     3     4     3     1
     2     4     6     2     6     2
     3     6    18     9     9    -6
     4     8    12    10    12     4
     5    10    24    11    15    -4

Reduced Row Echelon Form Matrix
     1     2     0     0     3     4
     0     0     1     0     0    -1
     0     0     0     1     0     0
     0     0     0     0     0     0
     0     0     0     0     0     0
```
