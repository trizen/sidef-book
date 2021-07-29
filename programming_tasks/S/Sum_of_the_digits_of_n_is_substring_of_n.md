[1]: https://rosettacode.org/wiki/Sum_of_the_digits_of_n_is_substring_of_n

# [Sum of the digits of n is substring of n][1]

```ruby
var upto = 1000
var base = 10
 
var list = (^upto -> grep {
    .digits(base).contains(.sumdigits(base).digits(base)...)
})
 
say "Numbers under #{upto} whose sum of digits is a substring of themselves:"
 
list.each_slice(8, {|*a|
    say a.map { '%3s' % _ }.join(' ')
})
 
say "\n#{list.len} such numbers found."
```

#### Output:
```
Numbers under 1000 whose sum of digits is a substring of themselves:
  0   1   2   3   4   5   6   7
  8   9  10  20  30  40  50  60
 70  80  90 100 109 119 129 139
149 159 169 179 189 199 200 300
400 500 600 700 800 900 910 911
912 913 914 915 916 917 918 919

48 such numbers found.
```
