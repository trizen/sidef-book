[1]: https://rosettacode.org/wiki/Humble_numbers

# [Humble numbers][1]

```ruby
func smooth_generator(primes) {
 
    var s = primes.len.of { [1] }
 
    {
        var n = s.map { .first }.min
        { |i|
            s[i].shift if (s[i][0] == n)
            s[i] << (n * primes[i])
        } * primes.len
        n
    }
}
 
with (smooth_generator([2,3,5,7])) {|g|
    say 50.of { g.run }.join(' ')
}
 
say "\nThe digit counts of humble numbers"
say '═'*35
 
with (smooth_generator([2,3,5,7])) {|g|
    for (var(d=1,c=0); d <= 20; ++c) {
        var n = g.run
        n.len > d || next
        say "#{'%10s'%c.commify}  have  #{'%2d'%d}  digit#{[:s,''][d==1]}"
        (c, d) = (0, n.len)
    }
}
```

#### Output:
```
1 2 3 4 5 6 7 8 9 10 12 14 15 16 18 20 21 24 25 27 28 30 32 35 36 40 42 45 48 49 50 54 56 60 63 64 70 72 75 80 81 84 90 96 98 100 105 108 112 120

The digit counts of humble numbers
═══════════════════════════════════
         9  have   1  digit
        36  have   2  digits
        95  have   3  digits
       197  have   4  digits
       356  have   5  digits
       579  have   6  digits
       882  have   7  digits
     1,272  have   8  digits
     1,767  have   9  digits
     2,381  have  10  digits
     3,113  have  11  digits
     3,984  have  12  digits
     5,002  have  13  digits
     6,187  have  14  digits
     7,545  have  15  digits
     9,081  have  16  digits
    10,815  have  17  digits
    12,759  have  18  digits
    14,927  have  19  digits
    17,323  have  20  digits
```
