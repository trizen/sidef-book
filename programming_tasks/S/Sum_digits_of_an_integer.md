[1]: https://rosettacode.org/wiki/Sum_digits_of_an_integer

# [Sum digits of an integer][1]

```ruby
func Σ(String str, base=36) {
    str.chars.map{ Num(_, base) }.sum
}
 
<1 1234 1020304 fe f0e DEADBEEF>.each { |n|
    say "Σ(#{n}) = #{Σ(n)}"
}
```

#### Output:
```
Σ(1) = 1
Σ(1234) = 10
Σ(1020304) = 10
Σ(fe) = 29
Σ(f0e) = 29
Σ(DEADBEEF) = 104
```