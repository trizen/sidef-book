[1]: https://rosettacode.org/wiki/N-queens_problem

# [N-queens problem][1]

```ruby
func N_queens_solution(N = 8) {
 
    func collision(field, row) {
        for i in (^row) {
            var distance = (field[i] - field[row])
            distance ~~ [0, row-i, i-row] && return true
        }
        return false
    }
 
    func search(field, row) {
        row == N && return field
        for i in (^N) {
            field[row] = i
            if (!collision(field, row)) {
                return (__FUNC__(field, row+1) || next)
            }
        }
        return []
    }
 
    for i in (0 .. N>>1) {
        if (var r = search([i], 1)) {
            return r
        }
    }
}
 
for n in (1..15) {
    say "#{'%2d' % n}: #{N_queens_solution(n) || 'No solution'}"
}
```

#### Output:
```
 1: [0]
 2: No solution
 3: No solution
 4: [1, 3, 0, 2]
 5: [0, 2, 4, 1, 3]
 6: [1, 3, 5, 0, 2, 4]
 7: [0, 2, 4, 6, 1, 3, 5]
 8: [0, 4, 7, 5, 2, 6, 1, 3]
 9: [0, 2, 5, 7, 1, 3, 8, 6, 4]
10: [0, 2, 5, 7, 9, 4, 8, 1, 3, 6]
11: [0, 2, 4, 6, 8, 10, 1, 3, 5, 7, 9]
12: [0, 2, 4, 7, 9, 11, 5, 10, 1, 6, 8, 3]
13: [0, 2, 4, 1, 8, 11, 9, 12, 3, 5, 7, 10, 6]
14: [0, 2, 4, 6, 11, 9, 12, 3, 13, 8, 1, 5, 7, 10]
15: [0, 2, 4, 1, 9, 11, 13, 3, 12, 8, 5, 14, 6, 10, 7]
```