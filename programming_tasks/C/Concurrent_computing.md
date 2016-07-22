[1]: http://rosettacode.org/wiki/Concurrent_computing

# [Concurrent computing][1]

A very basic threading support is provided by the *Block.fork()* method:

```ruby
<Enjoy Rosetta Code>            \
    .map{|str| {say str}.fork } \
    .map{|thr| thr.wait }
```

#### Output:
```
Enjoy
Code
Rosetta
```
