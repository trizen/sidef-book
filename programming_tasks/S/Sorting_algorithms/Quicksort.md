[1]: https://rosettacode.org/wiki/Sorting_algorithms/Quicksort

# [Sorting algorithms/Quicksort][1]

```ruby
func quicksort (a) {
    a.len < 2 && return(a)
    var p = a.pop_rand           # to avoid the worst cases
    __FUNC__(a.grep{ .< p}) + [p] + __FUNC__(a.grep{ .>= p})
}

say quicksort(rand(1..100, 10))
```
