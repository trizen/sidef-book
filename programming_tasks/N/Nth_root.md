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
 
say nthroot(5, 34);  # => 2.024397458501034082599817835297912829678
```


A minor optimization would be to calculate the successive _int(n-1)_ square roots of a number, then raise the result to the power of _2\*\*(int(n-1) / n)_.

```ruby
func nthroot_fast(n, a, precision=1e-5) {
  { a = nthroot(2, a, precision) } * int(n-1);
  a ** (2**int(n-1) / n);
}
 
say nthroot_fast(5, 34, 1e-64);  # => 2.024397458499885042510817245541937419115
```