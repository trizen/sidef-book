[1]: https://rosettacode.org/wiki/Vampire_number

# [Vampire number][1]

```ruby
func is_vampire (n) {
    return [] if n.ilog10.is_even
 
    var l1 = n.isqrt.ilog10.ipow10
    var l2 = n.isqrt
 
    var s = n.digits.sort.join
 
    gather {
        n.divisors.each { |d|
 
            d < l1 && next
            d > l2 && break
 
            var t = n/d
 
            next if (d%%10 && t%%10)
            next if ("#{d}#{t}".sort != s)
 
            take([d, t])
        }
    }
}
 
say "First 25 Vampire Numbers:"
 
with (1) { |i|
    for (var n = 1; i <= 25; ++n) {
        var fangs = is_vampire(n)
        printf("%2d. %6s : %s\n", i++, n, fangs.join(' ')) if fangs
    }
}
 
say "\nIndividual tests:"
 
[16758243290880, 24959017348650, 14593825548650].each { |n|
    var fangs = is_vampire(n)
    say "#{n}: #{fangs ? fangs.join(', ') : 'is not a vampire number'}"
}
```

#### Output:
```
First 25 Vampire Numbers:
 1.   1260 : [21, 60]
 2.   1395 : [15, 93]
 3.   1435 : [35, 41]
 4.   1530 : [30, 51]
 5.   1827 : [21, 87]
 6.   2187 : [27, 81]
 7.   6880 : [80, 86]
 8. 102510 : [201, 510]
 9. 104260 : [260, 401]
10. 105210 : [210, 501]
11. 105264 : [204, 516]
12. 105750 : [150, 705]
13. 108135 : [135, 801]
14. 110758 : [158, 701]
15. 115672 : [152, 761]
16. 116725 : [161, 725]
17. 117067 : [167, 701]
18. 118440 : [141, 840]
19. 120600 : [201, 600]
20. 123354 : [231, 534]
21. 124483 : [281, 443]
22. 125248 : [152, 824]
23. 125433 : [231, 543]
24. 125460 : [204, 615] [246, 510]
25. 125500 : [251, 500]

Individual tests:
16758243290880: [1982736, 8452080], [2123856, 7890480], [2751840, 6089832], [2817360, 5948208]
24959017348650: [2947050, 8469153], [2949705, 8461530], [4125870, 6049395], [4129587, 6043950], [4230765, 5899410]
14593825548650: is not a vampire number
```