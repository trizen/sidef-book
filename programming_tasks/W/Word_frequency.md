[1]: https://rosettacode.org/wiki/Word_frequency

# [Word frequency][1]

```ruby
var count = Hash()
var file = File(ARGV[0] \\ '135-0.txt')
 
file.open_r.each { |line|
    line.lc.scan(/[\pL]+/).each { |word|
        count{word} := 0 ++
    }
}
 
var top = count.sort_by {|_,v| v }.last(10).flip
 
top.each { |pair|
    say "#{pair.key}\t-> #{pair.value}"
}
```

#### Output:
```
the     -> 41088
of      -> 19949
and     -> 14942
a       -> 14596
to      -> 13951
in      -> 11214
he      -> 9648
was     -> 8621
that    -> 7924
it      -> 6661
```
