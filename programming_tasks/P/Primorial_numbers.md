[1]: https://rosettacode.org/wiki/Primorial_numbers

# [Primorial numbers][1]

```ruby
say (
    'First ten primorials: ',
    {|i| pn_primorial(i) }.map(^10).join(', ')
)

{ |i|
    say ("primorial(10^#{i}) has " + pn_primorial(10**i).len + ' digits')
} << 1..6
```

#### Output:
```
First ten primorials: 1, 2, 6, 30, 210, 2310, 30030, 510510, 9699690, 223092870
primorial(10^1) has 10 digits
primorial(10^2) has 220 digits
primorial(10^3) has 3393 digits
primorial(10^4) has 45337 digits
primorial(10^5) has 563921 digits
primorial(10^6) has 6722809 digits
```
