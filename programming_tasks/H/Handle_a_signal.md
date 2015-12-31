[1]: http://rosettacode.org/wiki/Handle_a_signal

# [Handle a signal][1]

```ruby
var start = Time.sec;
 
Sig.INT {
    Sys.say("Ran for #{Time.sec - start} seconds.");
    Sys.exit;
}
 
{ |i|
    Sys.say(i);
    Sys.sleep(0.5);
} * Math.inf;
```

#### Output:
```
1
2
3
4
^CRan for 2 seconds.
```
