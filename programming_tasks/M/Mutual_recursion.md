[1]: http://rosettacode.org/wiki/Mutual_recursion

# [Mutual recursion][1]

```ruby
func F(){}
func M(){}
 
F = func(n) { n > 0 ? (n - M(F(n-1))) : 1 }
M = func(n) { n > 0 ? (n - F(M(n-1))) : 0 }
 
[F, M].each { |seq|
    {|i| seq.call(i)}.map(^20).join(' ').say
}
```

#### Output:
```
1 1 2 2 3 3 4 5 5 6 6 7 8 8 9 9 10 11 11 12
0 0 1 2 2 3 4 4 5 6 6 7 7 8 9 9 10 11 11 12
```
