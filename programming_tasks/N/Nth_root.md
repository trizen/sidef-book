[1]: http://rosettacode.org/wiki/Nth_root

# [Nth root][1]

```ruby
func nthroot(n, a, precision=1e-5) {
  var x = 1;
  var prev = 0;
  while ((prev-x).abs > precision) {
    prev = x;
    x = (((n-1)*prev + a/(prev**(n-1))) / n);
  };
  return x;
}
 
say nthroot(5,34);  # => 2.024397458501034082599817835297912829678
```

A minor optimization would be to calculate the successive `n` square roots of a number, then raise the result at the power of `2**(int(n-1) / n)`.

```ruby
func nthroot_fast(n, a, precision=1e-5) {
  { a = nthroot(2, a, precision) } * int(n-1);
  a ** (2**int(n-1) / n);
}

say nthroot(5,34);  # => 2.024397458501034082599817835297912829678
```
