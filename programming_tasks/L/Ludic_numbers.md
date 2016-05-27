[1]: http://rosettacode.org/wiki/Ludic_numbers

# [Ludic numbers][1]

```ruby
func ludics_upto(nmax=100000) {
  Enumerator({ |collect|
    collect(1)
    var arr = 2..nmax
    while (arr) {
      collect(var n = arr[0])
      arr.range.by(n).each {|i| arr[i] = nil}
      arr.compact!
    }
  })
}
 
func ludics_first(n) {
    ludics_upto(n * n.log2).first(n)
}
 
say("First 25 Ludic numbers: ",     ludics_first(25).join(' '))
say("Ludics below 1000: ",          ludics_upto(1000).len)
say("Ludic numbers 2000 to 2005: ", ludics_first(2005).last(6).join(' '))
 
var a = ludics_upto(250).to_a
say("Ludic triples below 250: ", a.grep{|x| a.contains_all([x+2, x+6]) }
                                  .map {|x| '(' + [x, x+2, x+6].join(' ') + ')' }
                                  .join(' '))
```

#### Output:
```
First 25 Ludic numbers: 1 2 3 5 7 11 13 17 23 25 29 37 41 43 47 53 61 67 71 77 83 89 91 97 107
Ludics below 1000: 142
Ludic numbers 2000 to 2005: 21475 21481 21487 21493 21503 21511
Ludic triples below 250: (1 3 7) (5 7 11) (11 13 17) (23 25 29) (41 43 47) (173 175 179) (221 223 227) (233 235 239)
```