[1]: https://rosettacode.org/wiki/Find_square_difference

# [Find square difference][1]

```ruby
var N = 1000
 
# Binary search
var n = bsearch_ge(1, N, {|k|
    k**2 - (k-1)**2 <=> N+1
})
 
# Closed-form
var m = ceil((N + 1 + N&1) / 2)
 
assert(n**2 - (n-1)**2 > N)
assert_eq(n, m)
 
say "#{n}^2 - #{n-1}^2 = #{n**2 - (n-1)**2}"
```

#### Output:
```
501^2 - 500^2 = 1001
```
