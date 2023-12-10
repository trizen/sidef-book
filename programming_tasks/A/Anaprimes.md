[1]: https://rosettacode.org/wiki/Anaprimes

# [Anaprimes][1]

Up to 8 digits, takes about 30 seconds, using ~800 MB of RAM.

```ruby
for k in (3..8) {
    var P = primes(10**(k-1), 10**k).group_by{ Str(_).sort }
    var G = P.values
    var m = G.map{.len}.max
    printf("Largest group of anaprimes before %s: %s members.\n", commify(10**k), m)
    G.grep { .len == m }.sort.each {|group|
        say "First: #{group.head}  Last: #{group.tail}"
    }
    say ""
}
```

#### Output:
```
Largest group of anaprimes before 1,000: 4 members.
First: 149  Last: 941
First: 179  Last: 971
First: 379  Last: 937

Largest group of anaprimes before 10,000: 11 members.
First: 1237  Last: 7321
First: 1279  Last: 9721

Largest group of anaprimes before 100,000: 39 members.
First: 13789  Last: 98731

Largest group of anaprimes before 1,000,000: 148 members.
First: 123479  Last: 974213

Largest group of anaprimes before 10,000,000: 731 members.
First: 1235789  Last: 9875321

Largest group of anaprimes before 100,000,000: 4333 members.
First: 12345769  Last: 97654321
```
