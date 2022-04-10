[1]: https://rosettacode.org/wiki/Composite_numbers_k_with_no_single_digit_factors_whose_factors_are_all_substrings_of_k

# [Composite numbers k with no single digit factors whose factors are all substrings of k][1]

```ruby
var e = Enumerator({|f|
 
    var c = (9.primorial)
    var a = (1..c -> grep { .is_coprime(c) })
 
    loop {
        var n = a.shift
 
        a.push(n + c)
        n.is_composite || next
 
        f(n) if n.factor.all {|p| Str(n).contains(p) }
    }
})
 
var count = 10
 
e.each {|n|
    say n
    break if (--count <= 0)
}
```

#### Output:
```
15317
59177
83731
119911
183347
192413
1819231
2111317
2237411
3129361
```
