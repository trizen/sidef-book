[1]: http://rosettacode.org/wiki/Multifactorial

# [Multifactorial][1]

```ruby
func mfact(s, n) {
    n > 0 ? (n * mfact(s, n-s)) : 1;
}
 
1...10 each { |s|
    say "step=#{s}: #{1..10 map {|n| mfact(s, n)}.join(' ')}";
}
```