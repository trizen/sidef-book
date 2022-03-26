[1]: https://rosettacode.org/wiki/Sum_of_two_adjacent_numbers_are_primes

# [Sum of two adjacent numbers are primes][1]

```ruby
var wanted = (1..Inf -> lazy.map  {|n| [n, n+1, n+(n+1)] }\
                            .grep { .tail.is_prime })
 
wanted.first(20).each_2d {|a,b,c|
    printf("%2d + %2d = %2d\n", a,b,c)
}
```

#### Output:
```
 1 +  2 =  3
 2 +  3 =  5
 3 +  4 =  7
 5 +  6 = 11
 6 +  7 = 13
 8 +  9 = 17
 9 + 10 = 19
11 + 12 = 23
14 + 15 = 29
15 + 16 = 31
18 + 19 = 37
20 + 21 = 41
21 + 22 = 43
23 + 24 = 47
26 + 27 = 53
29 + 30 = 59
30 + 31 = 61
33 + 34 = 67
35 + 36 = 71
36 + 37 = 73
```
