[1]: https://rosettacode.org/wiki/Magic_squares_of_doubly_even_order

# [Magic squares of doubly even order][1]

```ruby
func double_even_magic_square(n) {
    assert(n%4 == 0, "Need multiple of four")
    var (bsize, max) = (n/4, n*n)
    var pre_pat = [true, false, false, true,
                   false, true, true, false]
    pre_pat += pre_pat.flip
    var pattern = (pre_pat.map{|b| bsize.of(b)... } * bsize)
    pattern.map_kv{|k,v| v ? k+1 : max-k }.slices(n)
}
 
func format_matrix(a) {
    var fmt = "%#{a.len**2 -> len}s"
    a.map { .map { fmt % _ }.join(' ') }.join("\n")
}
 
say format_matrix(double_even_magic_square(8))
```

#### Output:
```
 1  2 62 61 60 59  7  8
56 55 11 12 13 14 50 49
48 47 19 20 21 22 42 41
25 26 38 37 36 35 31 32
33 34 30 29 28 27 39 40
24 23 43 44 45 46 18 17
16 15 51 52 53 54 10  9
57 58  6  5  4  3 63 64
```