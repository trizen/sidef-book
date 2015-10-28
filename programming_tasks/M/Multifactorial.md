[1]: http://rosettacode.org/wiki/Multifactorial

# [Multifactorial][1]

```ruby
func mfact(s, n) {
    n > 0 ? (n * mfact(s, n-s)) : 1;
}
 
1...10 -> each { |s|
    say "step=#{s}: #{1...10 -> map {|n| mfact(s, n)}.join(' ')}";
}
```

#### Output:
```
step=1: 1 2 6 24 120 720 5040 40320 362880 3628800
step=2: 1 2 3 8 15 48 105 384 945 3840
step=3: 1 2 3 4 10 18 28 80 162 280
step=4: 1 2 3 4 5 12 21 32 45 120
step=5: 1 2 3 4 5 6 14 24 36 50
step=6: 1 2 3 4 5 6 7 16 27 40
step=7: 1 2 3 4 5 6 7 8 18 30
step=8: 1 2 3 4 5 6 7 8 9 20
step=9: 1 2 3 4 5 6 7 8 9 10
step=10: 1 2 3 4 5 6 7 8 9 10
```