[1]: https://rosettacode.org/wiki/One_of_n_lines_in_a_file

# [One of n lines in a file][1]

```ruby
func one_of_n(n) {
    var choice
    n.times { |i|
        choice = i if (1 > i.rand)
    }
    choice - 1
}
 
func one_of_n_test(n = 10, trials = 1_000_000) {
    var bins = []
    trials.times {
        bins[one_of_n(n)] := 0 ++
    }
    bins
}
 
say one_of_n_test()
```

#### Output:
```
99838 100843 99696 100078 99973 100350 100054 99495 99540 100133
```