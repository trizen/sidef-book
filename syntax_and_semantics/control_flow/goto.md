# goto

The `goto` statement is the most basic form of unconditional transfer of control.

```ruby
var i = 0

@:INCR i += 1
say "#{i} squared = #{i * i}"
goto :INCR if (i < 10)

say "Program Completed."
```

#### Output:

```
1 squared = 1
2 squared = 4
3 squared = 9
4 squared = 16
5 squared = 25
6 squared = 36
7 squared = 49
8 squared = 64
9 squared = 81
10 squared = 100
Program Completed.
```

Goto statements have been considered harmful by many computer scientists, notably Dijkstra.
