# goto

The `goto` statement is the most basic form of unconditional transfer of control.

```ruby
var i = 0

@:INCR i += 1
say "#{i} squared = #{i * i}"
goto :INCR if (i < 10)

say "Program Completed."
```

Goto statements have been considered harmful by many computer scientists, notably Dijkstra.
