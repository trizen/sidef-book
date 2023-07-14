[1]: https://rosettacode.org/wiki/Find_limit_of_recursion

# [Find limit of recursion][1]

Maximum recursion depth is memory dependent.

```ruby
func recurse(n) {
   say n
   recurse(n+1)
}
 
recurse(0)
```

#### Output:
```
0
1
2
...
...
357077
357078
357079
```
