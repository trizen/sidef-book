[1]: http://rosettacode.org/wiki/Factors_of_a_Mersenne_number

# [Factors of a Mersenne number][1]

```ruby
func mtest(b, p) {
    var bits = b.base(2).to_i.digits
    for (var sq = 1; bits; sq %= p) {
        sq *= sq;
        sq += sq if bits.shift.is_one
    }
    sq == 1
}

for m in (2..60 -> grep{.is_prime} + [929]) {
    var f = 0
    var x = (2**m - 1)
    var q
    Inf.times { |k|
        q = (2*k*m + 1)
        q%8 ~~ [1,7] || q.is_prime || next
        q*q > x || (f = mtest(m, q)) && break
    }
    say (f ? "M#{m} is composite with factor #{q}"
           : "M#{m} is prime")
}
```

#### Output:
```
M2 is prime
M3 is prime
M5 is prime
M7 is prime
M11 is composite with factor 23
M13 is prime
M17 is prime
M19 is prime
M23 is composite with factor 47
M29 is composite with factor 233
M31 is prime
M37 is composite with factor 223
M41 is composite with factor 13367
M43 is composite with factor 431
M47 is composite with factor 2351
M53 is composite with factor 6361
M59 is composite with factor 179951
M929 is composite with factor 13007
```
