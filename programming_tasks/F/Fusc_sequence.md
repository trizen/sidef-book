[1]: https://rosettacode.org/wiki/Fusc_sequence

# [Fusc sequence][1]

```ruby
func fusc(n) {
    static S = [0, 1]
    S[n] \\= (n.is_even ? S[n/2] : (S[(n-1)/2] + S[((n-1)/2)+1]))
}
 
say ("First 61 terms of the Stern-Brocot sequence: ", 61.of(fusc).join(' '))
 
say "\nIndex and value for first term longer than any previous:"
printf("%15s : %s\n", "Index", "Value");
 
var (index=0, len=0)
 
5.times {
    index = (index..Inf -> first_by { fusc(_).len > len })
    len = fusc(index).len
    printf("%15s : %s\n", index.commify, fusc(index).commify)
}
```

#### Output:
```
First 61 terms of the Stern-Brocot sequence: 0 1 1 2 1 3 2 3 1 4 3 5 2 5 3 4 1 5 4 7 3 8 5 7 2 7 5 8 3 7 4 5 1 6 5 9 4 11 7 10 3 11 8 13 5 12 7 9 2 9 7 12 5 13 8 11 3 10 7 11 4

Index and value for first term longer than any previous:
          Index : Value
              0 : 0
             37 : 11
          1,173 : 108
         35,499 : 1,076
        699,051 : 10,946
```
