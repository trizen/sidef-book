[1]: https://rosettacode.org/wiki/Solve_triangle_solitaire_puzzle

# [Solve triangle solitaire puzzle][1]

```ruby
const N = [0,1,1,1,1,1,1,1,1,1,1,1,1,1,1]

const G = [
    [ 0, 1, 3],[ 0, 2, 5],[ 1, 3, 6],
    [ 1, 4, 8],[ 2, 4, 7],[ 2, 5, 9],
    [ 3, 4, 5],[ 3, 6,10],[ 3, 7,12],
    [ 4, 7,11],[ 4, 8,13],[ 5, 8,12],
    [ 5, 9,14],[ 6, 7, 8],[ 7, 8, 9],
    [10,11,12],[11,12,13],[12,13,14],
]

const format = ({"#{' '*(5-_)}#{'%d '*_}\n"}.map(1..5).join + "\n")

func solve(n, i, g) is cached {
    i == N.end && return "Solved"
    n[g[1]] == 0 && return nil

    var s = given(n[g[0]]) {
        when(0) {
            n[g[2]] == 0 && return nil
            "#{g[2]} to #{g[0]}\n"
        }
        default {
            n[g[2]] == 1 && return nil
            "#{g[0]} to #{g[2]}\n"
        }
    }

    var a = n.clone
    g.each {|n| a[n] = 1-a[n] }
    var r = ''
    G.each {|g| (r = solve(a, i+1, g)) && break }
    r ? (s + (format % (a...)) + r) : r
}

format.printf(N...)

var r = ''
G.each {|g| (r = solve(N, 1, g)) && break }
say (r ? r : "No solution found")
```
