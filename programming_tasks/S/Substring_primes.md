[1]: https://rosettacode.org/wiki/Substring_primes

# [Substring primes][1]

Generic solution for any base &gt;= 2.

```ruby
func split_at_indices(array, indices) {
 
    var parts = []
    var i = 0
 
    for j in (indices) {
        parts << array.slice(i, j)
        i = j+1
    }
 
    parts
}
 
func consecutive_partitions(array, callback) {
    for k in (0..array.len) {
        combinations(array.len, k, {|*indices|
            var t = split_at_indices(array, indices)
            if (t.sum_by{.len} == array.len) {
                callback(t)
            }
        })
    }
}
 
func is_substring_prime(digits, base) {
 
    for k in (^digits) {
        digits.first(k+1).digits2num(base).is_prime || return false
    }
 
    consecutive_partitions(digits, {|part|
        part.all { .digits2num(base).is_prime } || return false
    })
 
    return true
}
 
func generate_from_prefix(p, base, digits) {
 
    var seq = [p]
 
    for d in (digits) {
        var t = [d, p...]
        if (is_prime(t.digits2num(base)) && is_substring_prime(t, base)) {
            seq << __FUNC__(t, base, digits)...
        }
    }
 
    return seq
}
 
func substring_primes(base) {     # finite sequence for each base >= 2
 
    var prime_digits = (base-1 -> primes)   # prime digits < base
 
    prime_digits.map  {|p| generate_from_prefix([p], base, prime_digits)... }\
                .map  {|t| digits2num(t, base) }\
                .sort
}
 
for base in (2..20) {
    say "base = #{base}: #{substring_primes(base)}"
}
```

#### Output:
```
base = 2: []
base = 3: [2]
base = 4: [2, 3, 11]
base = 5: [2, 3, 13, 17, 67]
base = 6: [2, 3, 5, 17, 23]
base = 7: [2, 3, 5, 17, 19, 23, 37]
base = 8: [2, 3, 5, 7, 19, 23, 29, 31, 43, 47, 59, 61, 157, 239, 251, 349, 379, 479, 491]
base = 9: [2, 3, 5, 7, 23, 29, 47]
base = 10: [2, 3, 5, 7, 23, 37, 53, 73, 373]
base = 11: [2, 3, 5, 7, 29, 79]
base = 12: [2, 3, 5, 7, 11, 29, 31, 41, 43, 47, 67, 71, 89, 137, 139, 359, 499, 503, 521, 569, 571, 809, 857, 859, 6043]
base = 13: [2, 3, 5, 7, 11, 29, 31, 37, 41, 67, 379]
base = 14: [2, 3, 5, 7, 11, 13, 31, 41, 47, 53, 73, 83, 101, 103, 109, 157, 167, 193, 439, 661, 1033, 2203]
base = 15: [2, 3, 5, 7, 11, 13, 37, 41, 43, 47, 107, 167, 197, 557, 617, 647]
base = 16: [2, 3, 5, 7, 11, 13, 37, 43, 53, 59, 61, 83, 179, 181, 211, 691, 947, 3389]
base = 17: [2, 3, 5, 7, 11, 13, 37, 41, 47, 53, 223, 631]
base = 18: [2, 3, 5, 7, 11, 13, 17, 41, 43, 47, 53, 59, 61, 67, 71, 97, 101, 103, 107, 131, 137, 139, 211, 239, 241, 251, 311, 313, 317, 751, 787, 859, 1069, 1103, 1109, 1213, 1223, 1283, 1289, 1759, 1831, 1861, 1871, 1931, 1933, 2371, 3803, 4349, 4523, 5639, 5647, 15467, 19867, 34807]
base = 19: [2, 3, 5, 7, 11, 13, 17, 41, 43, 59, 97, 211]
base = 20: [2, 3, 5, 7, 11, 13, 17, 19, 43, 47, 53, 59, 67, 71, 73, 79, 103, 107, 113, 151, 157, 223, 227, 233, 239, 263, 271, 277, 347, 353, 359, 383, 397, 1063, 1423, 1427, 1433, 1439, 1471, 1583, 1597, 3023, 4663, 4783, 5273, 5279, 7673, 28663]
```
