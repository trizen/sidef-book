[1]: https://rosettacode.org/wiki/Average_loop_length

# [Average loop length][1]

```ruby
func find_loop(n) {
    var seen = Hash()
    loop {
        with (irand(1, n)) { |r|
            seen.has(r) ? (return seen.len) : (seen{r} = true)
        }
    }
}
 
print " N    empiric      theoric      (error)\n";
print "===  =========  ============  =========\n";
 
define MAX    = 20
define TRIALS = 1000
 
for n in (1..MAX) {
    var empiric = (1..TRIALS -> sum { find_loop(n) } / TRIALS)
    var theoric = (1..n -> sum {|k| prod(n - k + 1 .. n) * k**2 / n**(k+1) })
 
    printf("%3d  %9.4f  %12.4f   (%5.2f%%)\n",
        n, empiric, theoric, 100*(empiric-theoric)/theoric)
}
```

#### Output:
```
 N    empiric      theoric      (error)
===  =========  ============  =========
  1     1.0000        1.0000   ( 0.00%)
  2     1.4990        1.5000   (-0.07%)
  3     1.8560        1.8889   (-1.74%)
  4     2.1730        2.2188   (-2.06%)
  5     2.5440        2.5104   ( 1.34%)
  6     2.7490        2.7747   (-0.93%)
  7     3.0390        3.0181   ( 0.69%)
  8     3.1820        3.2450   (-1.94%)
  9     3.4520        3.4583   (-0.18%)
 10     3.6580        3.6602   (-0.06%)
 11     3.9650        3.8524   ( 2.92%)
 12     3.9920        4.0361   (-1.09%)
 13     4.1270        4.2123   (-2.03%)
 14     4.3710        4.3820   (-0.25%)
 15     4.5520        4.5458   ( 0.14%)
 16     4.7120        4.7043   ( 0.16%)
 17     4.9400        4.8579   ( 1.69%)
 18     5.0070        5.0071   (-0.00%)
 19     5.2370        5.1522   ( 1.65%)
 20     5.2940        5.2936   ( 0.01%)
```
