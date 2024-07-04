[1]: https://rosettacode.org/wiki/Prime_numbers_whose_neighboring_pairs_are_tetraprimes

# [Prime numbers whose neighboring pairs are tetraprimes][1]

```ruby
func display(arr, p, f, g, type, limit, display_primes) {

    var s = arr.map(f).grep{.is_prime}
    print "Found #{s.len.commify} primes under #{limit.commify} whose #{type} neighboring pair are tetraprimes"

    if (display_primes) {
        say ':'
        s.slices(10).each{.map { "%#{limit.len+1}s" % _ }.join.say }
    }

    with (p) {|p|
        var c = s.count {|a| is_div(g(a), p) || is_div(g(g(a)), p) }
        say "\nof which #{c.commify} have a neighboring pair one of whose factors is #{p}.\n"
    }

    var D = s.diffs

    func median(a) {
        var l = a.len
        var j = l>>1
        l.is_even ? ((a[j-1] + a[j]) >> 1) : a[j]
    }

    say("Minimum gap between those #{s.len.commify} primes: ", D.min)
    say("Median  gap between those #{s.len.commify} primes: ", median(D.sort))
    say("Maximum gap between those #{s.len.commify} primes: ", D.max)
    say ''
}

for limit in (1e5, 1e6, 1e7) {
    var arr = 4.squarefree_almost_primes(limit).cons(2).grep_2d{|a,b| b-a == 1 }
    display(arr, 7, {.last.inc},  {.dec}, "preceding", limit, limit <= 1e5)
    display(arr, 7, {.first.dec}, {.inc}, "following", limit, limit <= 1e5)
}
```

#### Output:
```
Found 49 primes under 100,000 whose preceding neighboring pair are tetraprimes:
   8647  15107  20407  20771  21491  23003  23531  24767  24971  27967
  29147  33287  34847  36779  42187  42407  42667  43331  43991  46807
  46867  51431  52691  52747  53891  54167  58567  63247  63367  69379
  71711  73607  73867  74167  76507  76631  76847  80447  83591  84247
  86243  87187  87803  89387  93887  97547  97847  98347  99431

of which 31 have a neighboring pair one of whose factors is 7.

Minimum gap between those 49 primes: 56
Median  gap between those 49 primes: 1208
Maximum gap between those 49 primes: 6460

Found 46 primes under 100,000 whose following neighboring pair are tetraprimes:
   8293  16553  17389  18289  22153  26893  29209  33409  35509  36293
  39233  39829  40493  41809  45589  48109  58393  59629  59753  59981
  60493  60913  64013  64921  65713  66169  69221  71329  74093  75577
  75853  77689  77933  79393  79609  82913  84533  85853  87589  87701
  88681  91153  93889  96017  97381  98453

of which 36 have a neighboring pair one of whose factors is 7.

Minimum gap between those 46 primes: 112
Median  gap between those 46 primes: 1460
Maximum gap between those 46 primes: 10284

Found 885 primes under 1,000,000 whose preceding neighboring pair are tetraprimes
of which 503 have a neighboring pair one of whose factors is 7.

Minimum gap between those 885 primes: 4
Median  gap between those 885 primes: 756
Maximum gap between those 885 primes: 7712

Found 866 primes under 1,000,000 whose following neighboring pair are tetraprimes
of which 492 have a neighboring pair one of whose factors is 7.

Minimum gap between those 866 primes: 4
Median  gap between those 866 primes: 832
Maximum gap between those 866 primes: 10284

Found 10,815 primes under 10,000,000 whose preceding neighboring pair are tetraprimes
of which 5,176 have a neighboring pair one of whose factors is 7.

Minimum gap between those 10,815 primes: 4
Median  gap between those 10,815 primes: 648
Maximum gap between those 10,815 primes: 9352

Found 10,551 primes under 10,000,000 whose following neighboring pair are tetraprimes
of which 5,069 have a neighboring pair one of whose factors is 7.

Minimum gap between those 10,551 primes: 4
Median  gap between those 10,551 primes: 660
Maximum gap between those 10,551 primes: 10284
```
