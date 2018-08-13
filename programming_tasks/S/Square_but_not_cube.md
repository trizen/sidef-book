[1]: https://rosettacode.org/wiki/Square_but_not_cube

# [Square but not cube][1]

```ruby
var square_and_cube = Enumerator({|f|
    1..Inf -> each {|n| f(n**6) }
})
 
var square_but_not_cube = Enumerator({|f|
    1..Inf -> lazy.map {|n| n**2 }.grep {|n| !n.is_power(3) }.each {|n| f(n) }
})
 
say "First 30 positive integers that are a square but not a cube:"
say square_but_not_cube.first(30).join(' ')
 
say "First 15 positive integers that are both a square and a cube:"
say square_and_cube.first(15).join(' ')
```

#### Output:
```
First 30 positive integers that are a square but not a cube:
4 9 16 25 36 49 81 100 121 144 169 196 225 256 289 324 361 400 441 484 529 576 625 676 784 841 900 961 1024 1089
First 15 positive integers that are both a square and a cube:
1 64 729 4096 15625 46656 117649 262144 531441 1000000 1771561 2985984 4826809 7529536 11390625
```