[1]: https://rosettacode.org/wiki/Sub-unit_squares

# [Sub-unit squares][1]

Using the method described in the [OEIS entry](https://oeis.org/A061844), representing **(10^n - 1)/9** as a difference of squares **x^2 - y^2** and checking **x^2** to see if it satisfies the conditions.

```ruby
var N   = 20      # how many terms to compute
var arr = Set(1)

for n in (1..Inf) {
    var r = (10**n - 1)/9
    arr << r.diff_of_squares.map{.head}.map{.sqr.digits}.grep {|d|
        (d[-1] != 1) && d.none{.is_zero} && d.map{.dec}.digits2num.is_square
    }.map{.digits2num}...
    break if (arr.len >= N)
}

arr.sort.first(N).each_kv {|k,n|
    say "#{'%2d' % k+1}: #{n}"
}
```

#### Output:
```
 1: 1
 2: 36
 3: 3136
 4: 24336
 5: 5973136
 6: 71526293136
 7: 318723477136
 8: 264779654424693136
 9: 24987377153764853136
10: 31872399155963477136
11: 58396845218255516736
12: 517177921565478376336
13: 252815272791521979771662766736
14: 518364744896318875336864648336
15: 554692513628187865132829886736
16: 658424734191428581711475835136
17: 672475429414871757619952152336
18: 694688876763154697414122245136
19: 711197579293752874333735845136
20: 975321699545235187287523246336
```
