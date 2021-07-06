[1]: https://rosettacode.org/wiki/Numbers_with_prime_digits_whose_sum_is_13

# [Numbers with prime digits whose sum is 13][1]

```ruby
func generate_from_prefix(sum, p, base, digits) {
 
    var seq = [p]
 
    for d in (digits) {
        seq << __FUNC__(sum, [d, p...], base, digits)... if (p.sum+d <= sum)
    }
 
    return seq
}
 
func numbers_with_digitsum(sum, base = 10, digits = (base-1 -> primes)) {
 
    digits.map  {|p| generate_from_prefix(sum, [p], base, digits)... }\
          .map  {|t| digits2num(t, base) }\
          .grep {|t| t.sumdigits(base) == sum }\
          .sort
}
 
say numbers_with_digitsum(13)
```

#### Output:
```
[337, 355, 373, 535, 553, 733, 2227, 2272, 2335, 2353, 2533, 2722, 3235, 3253, 3325, 3352, 3523, 3532, 5233, 5323, 5332, 7222, 22225, 22252, 22333, 22522, 23233, 23323, 23332, 25222, 32233, 32323, 32332, 33223, 33232, 33322, 52222, 222223, 222232, 222322, 223222, 232222, 322222]
```
