[1]: http://rosettacode.org/wiki/Prime_conspiracy

# [Prime conspiracy][1]

```ruby
var primes = (^Inf -> lazy.grep{.is_prime})
 
var upto = 1e6
var conspiracy = Hash()
 
primes.first(upto+1).reduce { |a,b|
    var d = b%10
    conspiracy{"#{a} → #{d}"} := 0 ++
    d
}
 
for k,v in (conspiracy.sort_by{|k,_v| k }) {
    printf("%s count: %6s\tfrequency: %2.2f %\n", k, v.commify, v / upto * 100)
}
```

#### Output:
```
1 → 1 count: 42,853     frequency: 4.29 %
1 → 3 count: 77,475     frequency: 7.75 %
1 → 7 count: 79,453     frequency: 7.95 %
1 → 9 count: 50,153     frequency: 5.02 %
2 → 3 count:      1     frequency: 0.00 %
3 → 1 count: 58,255     frequency: 5.83 %
3 → 3 count: 39,668     frequency: 3.97 %
3 → 5 count:      1     frequency: 0.00 %
3 → 7 count: 72,828     frequency: 7.28 %
3 → 9 count: 79,358     frequency: 7.94 %
5 → 7 count:      1     frequency: 0.00 %
7 → 1 count: 64,230     frequency: 6.42 %
7 → 3 count: 68,595     frequency: 6.86 %
7 → 7 count: 39,603     frequency: 3.96 %
7 → 9 count: 77,586     frequency: 7.76 %
9 → 1 count: 84,596     frequency: 8.46 %
9 → 3 count: 64,371     frequency: 6.44 %
9 → 7 count: 58,130     frequency: 5.81 %
9 → 9 count: 42,843     frequency: 4.28 %
```
