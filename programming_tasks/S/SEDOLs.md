[1]: https://rosettacode.org/wiki/SEDOLs

# [SEDOLs][1]

```ruby
func sedol(s) {

    die 'No vowels allowed' if (s ~~ /[AEIOU]/)
    die 'Invalid format'    if (s !~ /^[0-9B-DF-HJ-NP-TV-Z]{6}$/)

    const base36 = [[(^10)..., ('A'..'Z')...], ^36].zip.flat.to_h
    const weights = [1, 3, 1, 7, 3, 9]

    var vs = [base36{ s.chars... }]
    var checksum = (vs ~Z* weights -> sum)
    var check_digit = ((10 - checksum%10) % 10)
    return (s + check_digit)
}

%w(
    710889
    B0YBKJ
    406566
    B0YBLH
    228276
    B0YBKL
    557910
    B0YBKR
    585284
    B0YBKT
    B00030
).each { |s|
    say sedol(s)
}
```

#### Output:
```
7108899
B0YBKJ7
4065663
B0YBLH2
2282765
B0YBKL9
5579107
B0YBKR5
5852842
B0YBKT7
B000300
```
