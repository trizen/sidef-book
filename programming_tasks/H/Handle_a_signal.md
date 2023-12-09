[1]: https://rosettacode.org/wiki/Handle_a_signal

# [Handle a signal][1]

```ruby
var start = Time.sec

Sig.INT {
    say "Ran for #{Time.sec - start} seconds."
    Sys.exit
}

{ |i|
    say i
    Sys.sleep(0.5)
} * Inf
```

#### Output:
```
1
2
3
4
^CRan for 2 seconds.
```
