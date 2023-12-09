[1]: https://rosettacode.org/wiki/Concurrent_computing

# [Concurrent computing][1]

A very basic threading support is provided by the `Block.fork()` method:

```ruby
var a = <Enjoy Rosetta Code>

a.map{|str|
    {   Sys.sleep(1.rand)
        say str
    }.fork
}.map{|thr| thr.wait }
```

#### Output:
```
Enjoy
Code
Rosetta
```
