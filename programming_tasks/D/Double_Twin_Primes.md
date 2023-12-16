[1]: https://rosettacode.org/wiki/Double_Twin_Primes

# [Double Twin Primes][1]

```ruby
1000.primes.each_cons(4, {|*a|
    if (a.diffs == [2, 4, 2]) {
        say a
    }
})
```

#### Output:
```
[5, 7, 11, 13]
[11, 13, 17, 19]
[101, 103, 107, 109]
[191, 193, 197, 199]
[821, 823, 827, 829]
```
