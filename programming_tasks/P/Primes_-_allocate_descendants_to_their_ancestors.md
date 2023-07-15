[1]: https://rosettacode.org/wiki/Primes_-_allocate_descendants_to_their_ancestors

# [Primes - allocate descendants to their ancestors][1]

```ruby
var maxsum = 99
var primes = maxsum.primes
 
var descendants = (maxsum+1).of { [] }
var ancestors   = (maxsum+1).of { [] }
 
for p in (primes) {
    descendants[p] << p
    for s in (1 .. descendants.end-p) {
        descendants[s + p] << descendants[s].map {|q| p*q }...
    }
}
 
for p in (primes + [4]) {
    descendants[p].pop
}
 
var total = 0
 
for s in (1 .. maxsum) {
 
    descendants[s].sort!
 
    total += (var dsclen = descendants[s].len)
    var idx = descendants[s].first_index {|x| x > maxsum }
 
    for d in (descendants[s].first(idx+1)) {
        ancestors[d] = (ancestors[s] + [s])
    }
 
    if ((s <= 20) || (s ~~ [46, 74, 99])) {
        printf("%2d: %d Ancestor(s): %-15s %5s Descendant(s): %s\n", s,
            ancestors[s].len, "[#{ancestors[s].join(' ')}]", descendants[s].len,
            dsclen <= 10 ? descendants[s] : "[#{descendants[s].first(10).join(' ')} ...]")
    }
}
 
say "\nTotal descendants: #{total}"
```

#### Output:
```
 1: 0 Ancestor(s): []                  0 Descendant(s): []
 2: 0 Ancestor(s): []                  0 Descendant(s): []
 3: 0 Ancestor(s): []                  0 Descendant(s): []
 4: 0 Ancestor(s): []                  0 Descendant(s): []
 5: 0 Ancestor(s): []                  1 Descendant(s): [6]
 6: 1 Ancestor(s): [5]                 2 Descendant(s): [8, 9]
 7: 0 Ancestor(s): []                  2 Descendant(s): [10, 12]
 8: 2 Ancestor(s): [5 6]               3 Descendant(s): [15, 16, 18]
 9: 2 Ancestor(s): [5 6]               4 Descendant(s): [14, 20, 24, 27]
10: 1 Ancestor(s): [7]                 5 Descendant(s): [21, 25, 30, 32, 36]
11: 0 Ancestor(s): []                  5 Descendant(s): [28, 40, 45, 48, 54]
12: 1 Ancestor(s): [7]                 7 Descendant(s): [35, 42, 50, 60, 64, 72, 81]
13: 0 Ancestor(s): []                  8 Descendant(s): [22, 56, 63, 75, 80, 90, 96, 108]
14: 3 Ancestor(s): [5 6 9]            10 Descendant(s): [33, 49, 70, 84, 100, 120, 128, 135, 144, 162]
15: 3 Ancestor(s): [5 6 8]            12 Descendant(s): [26 44 105 112 125 126 150 160 180 192 ...]
16: 3 Ancestor(s): [5 6 8]            14 Descendant(s): [39 55 66 98 140 168 189 200 225 240 ...]
17: 0 Ancestor(s): []                 16 Descendant(s): [52 88 99 147 175 210 224 250 252 300 ...]
18: 3 Ancestor(s): [5 6 8]            19 Descendant(s): [65 77 78 110 132 196 280 315 336 375 ...]
19: 0 Ancestor(s): []                 22 Descendant(s): [34 104 117 165 176 198 245 294 350 420 ...]
20: 3 Ancestor(s): [5 6 9]            26 Descendant(s): [51 91 130 154 156 220 264 297 392 441 ...]
46: 3 Ancestor(s): [7 10 25]         557 Descendant(s): [129 205 246 493 518 529 740 806 888 999 ...]
74: 5 Ancestor(s): [5 6 8 16 39]    6336 Descendant(s): [213 469 670 793 804 1333 1342 1369 1534 2014 ...]
99: 1 Ancestor(s): [17]            38257 Descendant(s): [194 1869 2225 2670 2848 3204 3237 4029 4565 5037 ...]

Total descendants: 546986
```
