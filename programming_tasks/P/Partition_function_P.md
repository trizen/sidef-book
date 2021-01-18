[1]: https://rosettacode.org/wiki/Partition_function_P

# [Partition function P][1]

Built-in:

```ruby
say partitions(6666)   # very fast
```


User-defined:

```ruby
func partitionsP(n) {
    func (n) is cached {
 
        n <= 1 && return n
 
        var a = sum(1..floor((sqrt(24*n + 1) + 1)/6), {|k|
            (-1)**(k-1) * __FUNC__(n - ((k*(3*k - 1)) >> 1))
        })
 
        var b = sum(1..ceil((sqrt(24*n + 1) - 7)/6), {|k|
            (-1)**(k-1) * __FUNC__(n - ((k*(3*k + 1)) >> 1))
        })
 
        a + b
    }(n+1)
}
 
var t = Time.micro
 
say partitionsP.map(0..25).join(' ')
say partitionsP(6666)
 
say ("Took %.4f seconds" % Time.micro-t)
```

#### Output:
```
1 1 2 3 5 7 11 15 22 30 42 56 77 101 135 176 231 297 385 490 627 792 1002 1255 1575 1958
193655306161707661080005073394486091998480950338405932486880600467114423441282418165863
Took 24.5225 seconds
```
