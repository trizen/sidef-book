[1]: https://rosettacode.org/wiki/Special_neighbor_primes

# [Special neighbor primes][1]

```ruby
func special_neighbor_primes(upto) {
    var list = []
    upto.primes.each_cons(2, {|p1,p2|
        var n = (p1 + p2 - 1)
        if (n.is_prime) {
            list << [p1, p2, n]
        }
    })
    return list
}
 
with (100) {|n|
    var list = special_neighbor_primes(n)
    say "Found #{list.len} special neighbour primes < n:"
    list.each_2d {|p1,p2,q|
        printf(" (%2s, %2s) => %s\n", p1, p2, q)
    }
}
 
say ''
 
for n in (1..7) {
    var list = special_neighbor_primes(10**n)
    say "Found #{list.len} special neighbour primes < 10^#{n}"
}
```

#### Output:
```
Found 13 special neighbour primes < n:
 ( 3,  5) => 7
 ( 5,  7) => 11
 ( 7, 11) => 17
 (11, 13) => 23
 (13, 17) => 29
 (19, 23) => 41
 (29, 31) => 59
 (31, 37) => 67
 (41, 43) => 83
 (43, 47) => 89
 (61, 67) => 127
 (67, 71) => 137
 (73, 79) => 151

Found 2 special neighbour primes < 10^1
Found 13 special neighbour primes < 10^2
Found 71 special neighbour primes < 10^3
Found 367 special neighbour primes < 10^4
Found 2165 special neighbour primes < 10^5
Found 14526 special neighbour primes < 10^6
Found 103611 special neighbour primes < 10^7
```
