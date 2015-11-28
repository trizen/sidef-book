[1]: http://rosettacode.org/wiki/Hofstadter_Q_sequence

# [Hofstadter Q sequence][1]

Using a memoized function:

```ruby
func Q(n) is cached {
    n <= 2 ? 1
           : Q(n - Q(n-1))+Q(n-Q(n-2))
}
 
say "First 10 terms: #{10.of {|n| Q(n) }.dump }"
say "Term 1000: #{Q(1000)}"
say "Terms less than preceding in first 100k: #{2..100000->count{|i|Q(i)<Q(i-1)}}"
```


Using an array:

```ruby
var Q = [0, 1, 1];
100_000.times {
    Q << (Q[-Q[-1]] + Q[-Q[-2]])
}
 
say "First 10 terms: #{Q.ft(1, 10).dump}"
say "Term 1000: #{Q[1000]}"
say "Terms less than preceding in first 100k: #{2..100000->count{|i|Q[i]<Q[i-1]}}"
```

#### Output:
```
First 10 terms: [1, 1, 2, 3, 3, 4, 5, 5, 6, 6]
Term 1000: 502
Terms less than preceding in first 100k: 49798
```