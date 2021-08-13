[1]: https://rosettacode.org/wiki/Odd_squarefree_semiprimes

# [Odd squarefree semiprimes][1]

```ruby
func odd_squarefree_almost_primes(upto, k=2) {
    k.squarefree_almost_primes(upto).grep{.is_odd}
}
 
with (1e3) {|n|
    var list = odd_squarefree_almost_primes(n, 2)
    say "Found #{list.len} odd square-free semiprimes <= #{n.commify}:"
    say (list.first(10).join(', '), ', ..., ', list.last(10).join(', '))
}
```

#### Output:
```
Found 194 odd square-free semiprimes <= 1,000:
15, 21, 33, 35, 39, 51, 55, 57, 65, 69, ..., 951, 955, 959, 965, 973, 979, 985, 989, 993, 995
```
