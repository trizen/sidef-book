[1]: https://rosettacode.org/wiki/Find_the_missing_permutation

# [Find the missing permutation][1]

```ruby
func check_perm(arr) {
    var hash = Hash()
    hash.set_keys(arr...)
    arr.each { |s|
        {
            var t = (s.substr(1) + s.substr(0, 1))
            hash.has_key(t) || return t
        } * s.len
    }
}
 
var perms = %w(ABCD CABD ACDB DACB BCDA ACBD ADCB CDAB DABC BCAD CADB CDBA
               CBAD ABDC ADBC BDCA DCBA BACD BADC BDAC CBDA DBCA DCAB)
 
say check_perm(perms)
```

#### Output:
```
DBAC
```
