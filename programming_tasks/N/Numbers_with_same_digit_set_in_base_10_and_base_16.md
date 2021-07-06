[1]: https://rosettacode.org/wiki/Numbers_with_same_digit_set_in_base_10_and_base_16

# [Numbers with same digit set in base 10 and base 16][1]

Simple solution:

```ruby
^1e5 -> grep { Set(.digits...) == Set(.digits(16)...) }.say
```


Recursively generate the numbers (2x faster):

```ruby
func generate_from_prefix(limit, p, base, digits) {
 
    var seq = [p]
 
    for d in (digits) {
        var t = [d, p...]
        if (t.digits2num(base) <= limit) {
            seq << __FUNC__(limit, t, base, digits)...
        }
    }
 
    return seq
}
 
func numbers_with_same_digitset(limit, base = 10) {
 
    (1..9).map  {|p| generate_from_prefix(limit, [p], base, @(0..9))... }\
          .map  {|t| digits2num(t, base) }\
          .grep {|t| Set(t.digits...) == Set(t.digits(base)...) }\
          .sort\
          .prepend(0)
}
 
say numbers_with_same_digitset(1e5, 16)
```

#### Output:
```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 53, 371, 913, 1040, 2080, 2339, 4100, 5141, 5412, 5441, 6182, 8200, 9241, 13593, 13665, 13969, 16406, 20530, 26946, 30979, 32803, 33638, 33840, 33841, 33842, 33843, 33844, 33845, 33846, 33847, 33848, 33849, 34883, 37943, 38931, 38966, 38995, 66310, 71444, 71497, 71511, 75120, 75121, 75122, 75123, 75124, 75125, 75126, 75127, 75128, 75129, 75621, 86150, 88165, 91465, 91769, 96617, 98711, 99481]
```
