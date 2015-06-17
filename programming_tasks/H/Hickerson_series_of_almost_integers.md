[1]: http://rosettacode.org/wiki/Hickerson_series_of_almost_integers

# [Hickerson series of almost integers][1]

```ruby
func h(n) {
    n! / (2 * Math.pow(2.log, n+1));
}
 
17.times { |n|
    "h(%2d) = %22s is%s almost an integer.\n".printf(
        n, var hn = h(n).roundf(-3), hn.to_s =~ /\.[09]/ ?? ? '' : ' NOT');
}
```

#### Output:
```
h( 1) =                  1.041 is almost an integer.
h( 2) =                  3.003 is almost an integer.
h( 3) =                 12.996 is almost an integer.
h( 4) =                 74.999 is almost an integer.
h( 5) =                541.002 is almost an integer.
h( 6) =               4683.001 is almost an integer.
h( 7) =              47292.999 is almost an integer.
h( 8) =             545834.998 is almost an integer.
h( 9) =            7087261.002 is almost an integer.
h(10) =          102247563.005 is almost an integer.
h(11) =         1622632572.998 is almost an integer.
h(12) =        28091567594.982 is almost an integer.
h(13) =       526858348381.001 is almost an integer.
h(14) =     10641342970443.085 is almost an integer.
h(15) =    230283190977853.037 is almost an integer.
h(16) =   5315654681981354.513 is NOT almost an integer.
h(17) = 130370767029135900.458 is NOT almost an integer.
```