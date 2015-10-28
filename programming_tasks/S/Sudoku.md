[1]: http://rosettacode.org/wiki/Sudoku

# [Sudoku][1]

```ruby
func _check(i, j) is cached {
    var (id, im) = i.divmod(9);
    var (jd, jm) = j.divmod(9);
 
    jd == id && return true;
    jm == im && return true;
 
    var id2 = int(id/3);
    var jd2 = int(jd/3);
 
    jd2 == id2 || return false;
 
    int(jm/3) == int(im/3)
}
 
func solve(board) {
    board.range.each { |i|
        board[i] && next;
        var t = board.items(
            board.range.grep {|j|
                _check(i, j)
            }...
        );
        1..9 -> grep {!(.~~t)}
             -> each {|k| board[i] = k; solve(board) };
        board[i] = 0;
        return;
    }
 
    board.range.each { |i|
        print "#{board[i]} ";
        print " "  if (3  -> divides(i+1));
        print "\n" if (9  -> divides(i+1));
        print "\n" if (27 -> divides(i+1));
    }
}
 
var board = %i(
    5 3 0  0 2 4  7 0 0
    0 0 2  0 0 0  8 0 0
    1 0 0  7 0 3  9 0 2
 
    0 0 8  0 7 2  0 4 9
    0 2 0  9 8 0  0 7 0
    7 9 0  0 0 0  0 8 0
 
    0 0 0  0 3 0  5 0 6
    9 6 0  0 1 0  3 0 0
    0 5 0  6 9 0  0 1 0
);
 
solve(board);
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