[1]: https://rosettacode.org/wiki/Abundant_odd_numbers

# [Abundant odd numbers][1]

```ruby
func is_abundant(n) {
    n.sigma > 2*n
}
 
func odd_abundants (from = 1) {
     from =  (from + 2)//3
     from += (from%2 - 1)
     3*from .. Inf `by` 6 -> lazy.grep(is_abundant)
}
 
say         " Index |      Number | proper divisor sum"
const sep = "-------+-------------+-------------------\n"
const fstr = "%6s | %11s | %11s\n"
 
print sep
 
odd_abundants().first(25).each_kv {|k,n|
    printf(fstr, k+1, n, n.sigma-n)
}
 
with (odd_abundants().nth(1000)) {|n|
    printf(sep + fstr, 1000, n, n.sigma-n)
}
 
with(odd_abundants(1e9).first) {|n|
    printf(sep + fstr, '***', n, n.sigma-n)
}
```

#### Output:
```
 Index |      Number | proper divisor sum
-------+-------------+-------------------
     1 |         945 |         975
     2 |        1575 |        1649
     3 |        2205 |        2241
     4 |        2835 |        2973
     5 |        3465 |        4023
     6 |        4095 |        4641
     7 |        4725 |        5195
     8 |        5355 |        5877
     9 |        5775 |        6129
    10 |        5985 |        6495
    11 |        6435 |        6669
    12 |        6615 |        7065
    13 |        6825 |        7063
    14 |        7245 |        7731
    15 |        7425 |        7455
    16 |        7875 |        8349
    17 |        8085 |        8331
    18 |        8415 |        8433
    19 |        8505 |        8967
    20 |        8925 |        8931
    21 |        9135 |        9585
    22 |        9555 |        9597
    23 |        9765 |       10203
    24 |       10395 |       12645
    25 |       11025 |       11946
-------+-------------+-------------------
  1000 |      492975 |      519361
-------+-------------+-------------------
   *** |  1000000575 |  1083561009
```
