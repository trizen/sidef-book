[1]: https://rosettacode.org/wiki/Calculating_the_value_of_e

# [Calculating the value of e][1]

```ruby
func calculate_e(n=50) {
    sum(0..n, {|k| 1/k! })
}

say calculate_e()
say calculate_e(69).as_dec(100)
```

#### Output:
```
2.7182818284590452353602874713526624977572470937
2.718281828459045235360287471352662497757247093699959574966967627724076630353547594571382178525166427
```

For finding the number of required terms for calculating `e` to a given number of decimal places, using the formula `Sum_{k=0..n} 1/k!`, we have:

```ruby
func f(n) {
    var t = n*log(10)
    (n + 10).bsearch_le { |k|
        lngamma(k+1) <=> t
    }
}

for k in (1..10) {
    var n = f(10**k)
    say "Sum_{k=0..#{n}} 1/k! = e correct to #{10**k->commify} decimal places"
}
```

#### Output:
```
Sum_{k=0..13} 1/k! = e correct to 10 decimal places
Sum_{k=0..69} 1/k! = e correct to 100 decimal places
Sum_{k=0..449} 1/k! = e correct to 1,000 decimal places
Sum_{k=0..3248} 1/k! = e correct to 10,000 decimal places
Sum_{k=0..25205} 1/k! = e correct to 100,000 decimal places
Sum_{k=0..205022} 1/k! = e correct to 1,000,000 decimal places
Sum_{k=0..1723507} 1/k! = e correct to 10,000,000 decimal places
Sum_{k=0..14842906} 1/k! = e correct to 100,000,000 decimal places
Sum_{k=0..130202808} 1/k! = e correct to 1,000,000,000 decimal places
Sum_{k=0..1158787577} 1/k! = e correct to 10,000,000,000 decimal places
```
