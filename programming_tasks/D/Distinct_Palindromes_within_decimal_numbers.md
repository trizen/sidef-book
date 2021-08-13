[1]: https://rosettacode.org/wiki/Distinct_Palindromes_within_decimal_numbers

# [Distinct Palindromes within decimal numbers][1]

```ruby
func palindromes(arr) {
    gather {
        for a in (0..arr.end), b in (a .. arr.end) {
            var sublist = arr.ft(a, b)
            take(sublist) if (sublist == sublist.flip)
        }
    }.uniq
}
 
for n in (100..125) {
    say "#{n} -> #{palindromes(n.digits).sort.map{.join}.sort_by{.len}.join(' ')}"
}
 
[9, 169, 12769, 1238769, 123498769, 12346098769, 1234572098769,
 123456832098769, 12345679432098769, 1234567905432098769, 123456790165432098769,
 83071934127905179083, 1320267947849490361205695, "amanaplanacanalpanama"].each {|n|
    var p = palindromes(n.kind_of(Number) ? n.digits : n.chars).grep { .len >= 2}
    say ("#{'%25s' % n} has #{'%2d' % p.len} palindromes of length 2 or more: ",
        p.sort.map{.join}.sort_by{.len}.join(' '))
}
```

#### Output:
```
100 -> 0 1 00
101 -> 0 1 101
102 -> 0 1 2
103 -> 0 1 3
104 -> 0 1 4
105 -> 0 1 5
106 -> 0 1 6
107 -> 0 1 7
108 -> 0 1 8
109 -> 0 1 9
110 -> 0 1 11
111 -> 1 11 111
112 -> 1 2 11
113 -> 1 3 11
114 -> 1 4 11
115 -> 1 5 11
116 -> 1 6 11
117 -> 1 7 11
118 -> 1 8 11
119 -> 1 9 11
120 -> 0 1 2
121 -> 1 2 121
122 -> 1 2 22
123 -> 1 2 3
124 -> 1 2 4
125 -> 1 2 5
                        9 has  0 palindromes of length 2 or more: 
                      169 has  0 palindromes of length 2 or more: 
                    12769 has  0 palindromes of length 2 or more: 
                  1238769 has  0 palindromes of length 2 or more: 
                123498769 has  0 palindromes of length 2 or more: 
              12346098769 has  0 palindromes of length 2 or more: 
            1234572098769 has  0 palindromes of length 2 or more: 
          123456832098769 has  0 palindromes of length 2 or more: 
        12345679432098769 has  0 palindromes of length 2 or more: 
      1234567905432098769 has  0 palindromes of length 2 or more: 
    123456790165432098769 has  0 palindromes of length 2 or more: 
     83071934127905179083 has  0 palindromes of length 2 or more: 
1320267947849490361205695 has  3 palindromes of length 2 or more: 202 494 949
    amanaplanacanalpanama has 12 palindromes of length 2 or more: aca ama ana nacan anacana lanacanal planacanalp aplanacanalpa naplanacanalpan anaplanacanalpana manaplanacanalpanam amanaplanacanalpanama
```
