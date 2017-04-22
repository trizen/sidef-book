[1]: http://rosettacode.org/wiki/Lychrel_numbers

# [Lychrel numbers][1]

```ruby
var (
    lychrels = [],
    palindromes = [],
    seeds = [],
    max = 500,
)
 
for i in (1 .. 10_000) {
    var (test = [], count = 0)
 
    func lychrel(l) {
        count++ > max && return true
        test << (var m = (l + Num(Str(l).flip)))
        Str(m).is_palindrome && return false
        lychrel(m)
    }
 
    if (lychrel(i)) {
        lychrels << Pair(Str(i), test)
    }
}
 
seeds << lychrels[0]
 
for l in lychrels {
    if (l.key.is_palindrome) {
        palindromes << l.key
    }
 
    var h = Hash()
    h.set_keys(l.value...)
 
    var trial = seeds.count_by { |s|
        s.value.any { |k| h.contains(k) } ? break : true
    }
 
    if (trial == seeds.len) {
        seeds << l
    }
}
 
say ("   Number of Lychrel seed numbers < 10_000: ", seeds.len)
say ("             Lychrel seed numbers < 10_000: ", seeds.map{.key}.join(', '))
say ("Number of Lychrel related numbers < 10_000: ", lychrels.len - seeds.len)
say ("    Number of Lychrel palindromes < 10_000: ", palindromes.len)
say ("              Lychrel palindromes < 10_000: ", palindromes.join(', '))
```

#### Output:
```
   Number of Lychrel seed numbers < 10_000: 5
             Lychrel seed numbers < 10_000: 196, 879, 1997, 7059, 9999
Number of Lychrel related numbers < 10_000: 244
    Number of Lychrel palindromes < 10_000: 3
              Lychrel palindromes < 10_000: 4994, 8778, 9999
```
