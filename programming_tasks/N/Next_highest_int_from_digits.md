[1]: https://rosettacode.org/wiki/Next_highest_int_from_digits

# [Next highest int from digits][1]

```ruby
func next_from_digits(n, b = 10) {
 
    var a = n.digits(b).flip
 
    while (a.next_permutation) {
        with (a.flip.digits2num(b)) { |t|
            return t if (t > n)
        }
    }
 
    return 0
}
 
say 'Next largest integer able to be made from these digits, or zero if no larger exists:'
 
for n in (
    0, 9, 12, 21, 12453, 738440, 3345333, 45072010,
    95322020, 982765431, 9589776899767587796600,
) {
    printf("%30s  ->  %s\n", n, next_from_digits(n))
}
```

#### Output:
```
Next largest integer able to be made from these digits, or zero if no larger exists:
                             0  ->  0
                             9  ->  0
                            12  ->  21
                            21  ->  0
                         12453  ->  12534
                        738440  ->  740348
                       3345333  ->  3353334
                      45072010  ->  45072100
                      95322020  ->  95322200
                     982765431  ->  983124567
        9589776899767587796600  ->  9589776899767587900667
```
