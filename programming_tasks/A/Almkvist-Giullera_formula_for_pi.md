[1]: https://rosettacode.org/wiki/Almkvist-Giullera_formula_for_pi

# [Almkvist-Giullera formula for pi][1]

```ruby
func almkvist_giullera(n) {
    (32 * (14*n * (38*n + 9) + 9) * (6*n)!) / (3 * n!**6)
}
 
func almkvist_giullera_pi(prec = 70) {
 
    local Num!PREC = (4*(prec+1)).numify
 
    var sum = 0
    var target = -1
 
    for n in (0..Inf) {
        sum += (almkvist_giullera(n) / (10**(6*n + 3)))
        var curr = (sum**-.5).as_dec
        return target if (target == curr)
        target = curr
    }
}
 
say 'First 10 integer portions: '
 
10.of {|n|
    say "#{n} #{almkvist_giullera(n)}"
}
 
with(70) {|n|
    say "π to #{n} decimal places is:"
    say almkvist_giullera_pi(n)
}
```

#### Output:
```
First 10 integer portions: 
0 96
1 5122560
2 190722470400
3 7574824857600000
4 312546150372456000000
5 13207874703225491420651520
6 567273919793089083292259942400
7 24650600248172987140112763715584000
8 1080657854354639453670407474439566400000
9 47701779391594966287470570490839978880000000
π to 70 decimal places is:
3.1415926535897932384626433832795028841971693993751058209749445923078164
```
