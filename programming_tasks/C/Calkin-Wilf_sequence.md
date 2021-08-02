[1]: https://rosettacode.org/wiki/Calkin-Wilf_sequence

# [Calkin-Wilf sequence][1]

```ruby
func calkin_wilf(n) is cached {
    return 1 if (n == 1)
    1/(2*floor(__FUNC__(n-1)) + 1 - __FUNC__(n-1))
}
 
func r2cw(r) {
 
    var cfrac = r.as_cfrac
    cfrac.len.is_odd || return nil
 
    Num(cfrac.flip.map_kv {|k,v| (k.is_odd ? '0' : '1') * v }.join, 2)
}
 
with (20) {|n|
    say "First #{n} terms of the Calkin-Wilf sequence:"
    say calkin_wilf.map(1..n)
}
 
with (83116/51639) {|r|
    say ("\n#{r.as_rat} is at index: ", r2cw(r))
}
```

#### Output:
```
First 20 terms of the Calkin-Wilf sequence:
[1, 1/2, 2, 1/3, 3/2, 2/3, 3, 1/4, 4/3, 3/5, 5/2, 2/5, 5/3, 3/4, 4, 1/5, 5/4, 4/7, 7/3, 3/8]

83116/51639 is at index: 123456789
```
